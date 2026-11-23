# ADR-004: Authentifizierung über Schnittstelle mit Test-Login, LDAP-Adapter später

> **Status:** Vorgeschlagen
> **Datum:** 23.11.2026
> **Beteiligt:** Rico Mauksch, KI-Agent (Claude Code)

## Kontext
Laut `docs/product/overview.md` erfolgt die Anmeldung über das LDAP-System der Fakultät, die S-Nummer ist
das Benutzerkennzeichen. Das Team geht nicht davon aus, im Projekt direkten Zugang zum LDAP der HTW zu
bekommen. Ob die Hochschule stattdessen ein Single Sign-on (z. B. Shibboleth) anbietet, ist unbekannt.

Beim Login sind drei Fragen zu unterscheiden:
1. **Wer ist die Person?** (Authentifizierung) – das beantwortet LDAP.
2. **Welche Rolle hat sie?** (Studierende, Professor, Administration) – ob LDAP-Gruppen das liefern, ist unklar.
3. **Darf sie sich bewerben?** (`Eligibility`: Fachsemester, Wiederholer) – steht voraussichtlich nicht im LDAP.

## Entscheidung
Die Authentifizierung liegt **hinter einer Schnittstelle** (`AuthenticationService` in `src/application/`).
Im Projekt gibt es zunächst nur einen **Test-Login** (`DevAuthenticationService` in `src/infrastructure/`)
mit festen Testnutzern je Rolle. Ein echter LDAP-Adapter (`LdapAuthenticationService`) kann später ergänzt
werden, ohne den Rest der Anwendung zu ändern.

Login und Sitzung in Next.js übernimmt **Auth.js** mit einem Anmeldeformular (S-Nummer und Passwort),
das den `AuthenticationService` aufruft.

**Rolle und Berechtigung** verwaltet die Anwendung selbst in ihrer Datenbank, nicht das LDAP.

## Alternativen
| Alternative | Vorteile | Nachteile | Warum nicht |
| --- | --- | --- | --- |
| Von Anfang an echtes HTW-LDAP | Realistisch ab dem ersten Tag | Zugang, VPN und Freigabe nötig; Tests hängen am Hochschulnetz; echte Konten in Tests | Zugang ist voraussichtlich nicht zu bekommen |
| Hochschul-SSO (z. B. Shibboleth) | Anwendung sieht keine Passwörter | Registrierung bei der Hochschul-IT nötig; weicht von „LDAP“ in `overview.md` ab | Nicht bekannt, ob angeboten |
| Eigene Benutzerverwaltung mit Passwörtern | Unabhängig von der Hochschule | Widerspricht der Vorgabe; Passwörter müssten selbst sicher verwaltet werden | Nicht gewünscht |

## Konsequenzen
- Positiv: Das Team kann sofort entwickeln und testen, ohne Hochschulnetz und ohne echte Zugangsdaten.
- Positiv: Ein späterer Wechsel zu LDAP oder SSO betrifft nur einen Adapter in `src/infrastructure/`.
- Negativ: Die echte Anbindung wird im Projekt voraussichtlich nicht geprüft.
- Zu beachten: Der Test-Login darf nur über eine Umgebungsvariable aktiviert werden und muss außerhalb der lokalen Entwicklung abgeschaltet sein.
- Zu beachten: Rollen und Berechtigungen werden bei jeder geschützten Aktion auf dem Server geprüft (siehe ADR-001).
- Zu beachten: Auth.js ist eine neue Abhängigkeit; für den späteren LDAP-Adapter käme eine LDAP-Bibliothek (z. B. `ldapts`) hinzu.
- Offen (Feature 001, #22): Wie kommt die Anwendung an Rolle und Berechtigung, z. B. über eine Liste zugelassener S-Nummern, die die Administration pflegt?
- Offen (mit der Fakultät zu klären): LDAP-Server und Zugangsweg, Rollen über LDAP-Gruppen, Verfügbarkeit von SSO.

## KI-Unterstützung
Die KI hat die Unterscheidung zwischen Authentifizierung, Rolle und Berechtigung aufgezeigt, drei Optionen
verglichen und die Schnittstelle mit Test-Login empfohlen. Das Team ist der Empfehlung gefolgt, weil
direkter LDAP-Zugang nicht zu erwarten ist und die SSO-Möglichkeit unbekannt ist.
