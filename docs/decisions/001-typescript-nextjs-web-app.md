# ADR-001: Eine Web-Anwendung mit TypeScript und Next.js

> **Status:** Vorgeschlagen
> **Datum:** 23.11.2026
> **Beteiligt:** Rico Mauksch

## Kontext
Drei Rollen greifen auf das System zu: Studierende (Projektseminare ansehen, Wünsche und Motivationsschreiben
einreichen), Professoren (Projektseminare mit PDF-Beschreibung und Platzkapazität bereitstellen) und die
Administration (Bewerbungen auswerten, Studierende zuteilen). Alle drei arbeiten auf denselben Daten:
Das Projektseminar, das ein Professor anlegt, ist genau das, was Studierende auswählen.

Vorgaben aus `docs/product/overview.md`: geschützter Zugang, rollenbasierte Berechtigungen, responsive Website
statt eigener App. Die erwartete Last ist gering (einige hundert Bewerbungen pro Vergaberunde).
Die Anwendung soll zunächst nur lokal laufen. Das Team arbeitet mit Coding-Agenten (OpenCode) und
braucht deshalb einen verbreiteten, gut dokumentierten Stack und eine Codebasis, die ein Agent als Ganzes überblickt.

## Entscheidung
Wir bauen **eine einzige Web-Anwendung in TypeScript mit Next.js** (App Router). Alle Rollen nutzen dieselbe
Anwendung; nach der Anmeldung sieht jede Person nur die Bereiche ihrer Rolle. Berechtigungen werden
**auf dem Server** geprüft, nicht nur durch Ausblenden in der Oberfläche.

Die Vier-Schichten-Struktur aus `AGENTS.md` bleibt erhalten:
- `src/domain/` und `src/application/` sind reines TypeScript ohne Abhängigkeit zu Next.js, Datenbank oder Oberfläche.
- Next.js gehört ausschließlich zur Schicht `presentation`.

## Alternativen
| Alternative | Vorteile | Nachteile | Warum nicht |
| --- | --- | --- | --- |
| Ein Backend (NestJS) mit zwei Oberflächen (Studierenden- und Verwaltungsportal) | Klare Trennung der Oberflächen, Verwaltungsportal separat absicherbar | Drei Projekte mit eigenem Build, Test und Deployment; geteilte Typen nötig | Aufwand steht in keinem Verhältnis zur Last; Rollen arbeiten auf denselben Daten |
| Ein Backend (NestJS) mit einer React-Oberfläche | Saubere Trennung Frontend/Backend | Zwei Projekte, API-Vertrag muss gepflegt werden | Kein Mehrwert gegenüber einer Anwendung bei dieser Größe |
| Python (z. B. FastAPI) mit serverseitigem Rendering | Passt zu den Python-Beispielen in `templates/examples/` | – | Team hat sich für TypeScript entschieden |

## Konsequenzen
- Positiv: Ein Repository, ein Build, ein Testlauf. Ein Agent sieht den gesamten Ablauf von Oberfläche bis Datenbank.
- Positiv: Eine Sprache für Oberfläche und Serverlogik; Typen aus der Domain sind überall nutzbar.
- Negativ: Ein eigenes Verwaltungsportal (z. B. nur im Hochschulnetz erreichbar) ist nicht von Anfang an vorgesehen. Es lässt sich nachrüsten, ohne `domain/` und `application/` zu ändern.
- Zu beachten: Next.js erwartet die Routen in `src/app/`. Diese Routen zählen zur Schicht `presentation` und bleiben dünn: Eingaben annehmen, Anwendungsfall aus `src/application/` aufrufen, Ergebnis anzeigen. Die genaue Ordneraufteilung legt der erste Plan fest.
- Zu beachten: Die Beispiele in `templates/examples/` sind in Python geschrieben und dienen nur als inhaltliche Vorlage.
- Offen: Test-Framework und Befehle (Tests, Starten, Linting) werden beim Aufsetzen des Projekts in `AGENTS.md` eingetragen.

## KI-Unterstützung
Die KI hat drei Architekturvarianten (eine Anwendung, ein Backend mit zwei Oberflächen, ein Backend mit einer Oberfläche)
mit Vor- und Nachteilen aufgestellt und die eine Anwendung empfohlen. Die Sprache hat das Team selbst festgelegt
(TypeScript statt des von der KI vorgeschlagenen Python); der Empfehlung zur Architekturvariante ist es gefolgt.
