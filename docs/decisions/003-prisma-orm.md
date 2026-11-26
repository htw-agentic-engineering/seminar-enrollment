# ADR-003: Prisma als ORM

> **Status:** Vorgeschlagen
> **Datum:** 23.11.2026
> **Beteiligt:** Rico Mauksch

## Kontext
Die Anwendung (ADR-001) greift auf PostgreSQL (ADR-002) zu. Das Datenbankschema wird sich im Laufe
des Projekts ändern, z. B. durch neue Features wie das Bearbeiten bis Fristende (#33). Mehrere Personen
und Agenten arbeiten parallel daran. Fehler wie falsche Tabellen- oder Feldnamen sollen früh auffallen,
nicht erst zur Laufzeit.

## Entscheidung
Wir verwenden **Prisma** als ORM. Prisma liefert typsichere Datenbankzugriffe, ein zentrales Schema
und versionierte Migrationen.

Prisma wird **nur in `src/infrastructure/`** verwendet. Die Domain kennt Prisma nicht:
`src/application/` definiert Repository-Schnittstellen (z. B. `ApplicationRepository`),
`src/infrastructure/` implementiert sie mit Prisma (z. B. `PrismaApplicationRepository`).

## Alternativen
| Alternative | Vorteile | Nachteile | Warum nicht |
| --- | --- | --- | --- |
| Drizzle | Schlank, Schema direkt in TypeScript, nah an SQL | Weniger verbreitet; Agenten kennen es weniger gut | Prisma ist für das Team und die Agenten besser dokumentiert |
| Kysely | Typsicheres SQL, volle Kontrolle | Kein ORM, Migrationen nur rudimentär | Mehr Handarbeit bei Migrationen |
| Reines SQL (`pg`) | Kein zusätzliches Werkzeug | Keine Typsicherheit, Migrationen selbst bauen | Zu fehleranfällig bei parallelem Arbeiten |

## Konsequenzen
- Positiv: Der Compiler erkennt falsche Tabellen- und Feldnamen, auch wenn ein Agent sie erfindet.
- Positiv: Schemaänderungen werden als Migrationsdateien versioniert; jeder bringt seine Datenbank mit einem Befehl auf den aktuellen Stand.
- Negativ: Prisma-Modelle und Domain-Objekte sind getrennt; in den Repositories muss zwischen beiden umgewandelt werden.
- Zu beachten: Prisma-Typen dürfen nicht in `src/domain/` oder `src/application/` auftauchen.
- Zu beachten: Feldnamen im Schema folgen dem Glossar (`docs/product/glossary.md`).

## KI-Unterstützung
Die KI hat erklärt, wozu ein ORM in dieser Architektur dient, vier Optionen verglichen und Prisma empfohlen.
Das Team ist der Empfehlung gefolgt.
