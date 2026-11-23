# ADR-002: PostgreSQL als Datenbank

> **Status:** Vorgeschlagen
> **Datum:** 23.11.2026
> **Beteiligt:** Rico Mauksch, KI-Agent (Claude Code)

## Kontext
Das System muss Projektseminare, Platzkapazitäten, Bewerbungen mit Erst-, Zweit- und Drittwunsch,
Motivationsschreiben und Zuteilungen dauerhaft speichern. Bewerbungen und Motivationsschreiben sind
personenbezogene Daten. Die erwartete Last ist gering, kurz vor Ende der Bewerbungsfrist können aber
viele Studierende gleichzeitig speichern und einreichen. Die Anwendung läuft zunächst lokal.

## Entscheidung
Wir verwenden **PostgreSQL** als Datenbank. Lokal läuft sie in einem Docker-Container, damit alle
Teammitglieder dieselbe Version und Konfiguration nutzen.

## Alternativen
| Alternative | Vorteile | Nachteile | Warum nicht |
| --- | --- | --- | --- |
| SQLite | Keine Installation, eine Datei, sehr schnelle Tests | Schwächer bei gleichzeitigen Schreibzugriffen; Wechsel zu einem Server später nötig | Team will von Anfang an mit einer produktionsnahen Datenbank arbeiten |
| MySQL/MariaDB | Ebenfalls verbreitet, an Hochschulen häufig vorhanden | Kein Vorteil gegenüber PostgreSQL für diesen Anwendungsfall | Kein Grund für einen Wechsel |

## Konsequenzen
- Positiv: Produktionsnah von Anfang an; zuverlässig bei gleichzeitigen Einreichungen kurz vor Fristende.
- Positiv: Kein späterer Datenbankwechsel nötig, falls die Anwendung auf einem Server betrieben wird.
- Negativ: Jedes Teammitglied braucht Docker (bzw. eine lokale PostgreSQL-Installation). Docker ist damit eine neue Voraussetzung für die Entwicklung.
- Negativ: Tests gegen die Datenbank sind langsamer als mit SQLite. Fachliche Regeln werden deshalb in `src/domain/` ohne Datenbank getestet.
- Zu beachten: Der Datenbankzugriff liegt nur in `src/infrastructure/` (siehe ADR-003).
- Zu beachten: Im Projekt werden ausschließlich Testdaten verwendet, keine echten Studierendendaten.

## KI-Unterstützung
Die KI hat SQLite wegen der geringen Last und der einfachen Einrichtung empfohlen. Das Team hat sich
bewusst für PostgreSQL entschieden, um produktionsnah zu arbeiten.
