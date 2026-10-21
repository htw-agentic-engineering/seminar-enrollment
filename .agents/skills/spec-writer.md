# Skill: spec-writer

## Zweck

Eine neue Spezifikation nach der Teamvorlage anlegen — strukturiert, vollständig, ohne gleich in die Umsetzung zu springen.

## Wann passt dieser Skill

Wenn ein neues Feature entwickelt werden soll und noch keine Spec dafür existiert.
Typischer Auslöser: ein GitHub Issue ist angelegt, jetzt soll die Spec dazu entstehen.

## Ablauf

1. Frage nach dem Feature-Namen, der Nummer und dem zugehörigen GitHub Issue (z. B. `#12`)
2. Kopiere `templates/spec.md` nach `docs/specs/00X-<feature-name>/spec.md`
3. Fülle gemeinsam mit dem Entwickler aus: Ziel, Beteiligte, erste User Story
4. Trage das GitHub Issue unter "Feature-Issue" ein
5. Leg die Datei auf dem aktuellen Feature-Branch ab
6. Noch kein Code — warte auf Review und Freigabe durch das Team

## Was dabei nicht gemacht wird

- Keinen Code schreiben, keinen Plan erstellen — das kommt erst nach dem Spec-Review
- Keine Felder erfinden oder raten — lieber nachfragen
