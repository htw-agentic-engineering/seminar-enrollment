# workflow-kit

Vorlage für ein Agentic-Engineering-Projekt in der Lehre.
Entsteht im Projektseminar Agentic Engineering an der HTW Dresden (WS 2026/27).

> Work in progress – noch nicht für den Einsatz in Lehrveranstaltungen gedacht.

## Nutzung
Auf **Use this template** klicken. Das neue Repo ist fertig eingerichtet für die Arbeit mit einem Coding-Agenten (z. B. OpenCode).

## Aufbau

| Ort | Inhalt |
| --- | --- |
| `AGENTS.md` | Einstieg für den Agenten: Befehle, Struktur, Regeln, Verweise |
| `opencode.json` | Bindet Glossar und Teamcharta automatisch in jede Agenten-Sitzung ein |
| `.github/` | Issue-Vorlagen (Stufe 2 und 3) und Pull-Request-Vorlage |
| `docs/product/` | Produktüberblick (Vision, Rollen, Personas, Features) und Glossar |
| `docs/team/TEAM_CHARTA.md` | Teamcharta: Regeln für die Zusammenarbeit |
| `docs/specs/` | Spezifikation und Plan pro Feature |
| `docs/decisions/` | Architekturentscheidungen |
| `docs/workflow/` | Leitfäden: welche Stufe wann, gute Anfragen, Ablauf mit Spezifikationen |
| `templates/` | Vorlagen zum Kopieren: Spezifikation, Plan, ADR, dazu ausgefüllte Beispiele in `templates/examples/` |
| `src/`, `tests/` | Code in vier Schichten und Tests |

## So arbeiten wir
1. **Produkt klären:** `docs/product/overview.md` und `glossary.md` ausfüllen
2. **Technik entscheiden:** ADRs schreiben, `AGENTS.md` ausfüllen
3. **Änderungen einstufen** nach dem [Leitfaden](docs/workflow/when-to-use-what.md):
   - Stufe 1: direkter Prompt
   - Stufe 2: Issue „Kleine Änderung“
   - Stufe 3: Issue „Feature“, dann Spezifikation und Plan ([Ablauf](docs/workflow/spec-workflow.md))
4. **Umsetzen:** Branch → Agent → selbst prüfen → Pull Request → Review → Merge

## Für das Projektteam
- `notes/` enthält interne Notizen und wird vor der Weitergabe entfernt
