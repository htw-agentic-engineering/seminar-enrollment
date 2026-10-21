# ADR-001: SQLite als Datenbank

> **Status:** Angenommen
> **Datum:** 28.10.
> **Beteiligt:** gesamtes Team

<!-- BEISPIEL: So kann ein ausgefüllter ADR aussehen. -->

## Kontext
Das Ausleihsystem muss Geräte, Personen und Ausleihen dauerhaft speichern. Es wird von einem Labor mit
etwa 200 Geräten und wenigen gleichzeitigen Nutzern verwendet. Das Team hat wenig Erfahrung mit dem
Betrieb von Datenbankservern, und alle sollen das Projekt ohne Zusatzinstallation lokal starten können.

## Entscheidung
Wir verwenden **SQLite** als Datenbank.

## Alternativen
| Alternative | Vorteile | Nachteile | Warum nicht |
| --- | --- | --- | --- |
| PostgreSQL | Für viele gleichzeitige Nutzer ausgelegt, viele Funktionen | Eigener Server nötig, aufwendigere Einrichtung für alle | Für die erwartete Last nicht nötig |
| JSON-Datei | Kein Datenbankwissen nötig | Keine Abfragen, Gefahr von Datenverlust bei gleichzeitigem Schreiben | Zu fehleranfällig für Ausleihen |

## Konsequenzen
- Positiv: Keine Installation, die Datenbank ist eine einzelne Datei, Tests laufen schnell.
- Negativ: Bei deutlich mehr gleichzeitigen Nutzern müsste auf einen Datenbankserver gewechselt werden.
- Zu beachten: Der Datenbankzugriff liegt nur in `src/infrastructure/`. Ein späterer Wechsel betrifft dann nur diese Schicht.

## KI-Unterstützung
Die KI hat die drei Optionen mit Vor- und Nachteilen aufgestellt. Die Kriterien (lokal ohne Installation
startbar, erwartete Last) hat das Team selbst festgelegt; danach war die Entscheidung eindeutig.
