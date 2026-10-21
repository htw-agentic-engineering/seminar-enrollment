# Skills

Hier liegen modulare Arbeitsanweisungen für Agenten — keine Dokumentation fürs Team-Review, sondern konkrete Schritt-für-Schritt-Anleitungen, die ein Agent bei einer bestimmten Aufgabe abarbeitet.

Der Ordner heißt `.agents/`, damit klar ist: das hier ist für den Agenten, nicht für Menschen.
Er funktioniert mit jedem Tool (OpenCode, Claude Code, Cursor usw.), weil er an keinen Anbieter gebunden ist.

## Wie man einen Skill aufruft

Entweder explizit:
```
Führe den Skill `.agents/skills/spec-writer.md` aus.
```
Oder der Agent erkennt selbst, dass ein Skill passt (z. B. beim Anlegen einer neuen Spec).

## Verfügbare Skills

| Skill | Wann benutzen |
|-------|---------------|
| `spec-writer.md` | Wenn eine neue Spezifikation angelegt werden soll |

## Neuen Skill hinzufügen

Neue Datei anlegen, Namensschema: `<was-der-skill-tut>.md`.
Struktur: **Zweck** → **Wann passt der Skill** → **Schritt-für-Schritt-Ablauf** → **Was dabei nicht gemacht werden soll**.
