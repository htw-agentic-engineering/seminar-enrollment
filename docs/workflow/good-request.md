# Was macht eine gute Anfrage an einen Agenten aus?

Eine gute Anfrage enthält genau das, was der Agent nicht selbst herausfinden kann – und nicht mehr.

## Was hineingehört

- **Ziel und Zweck:** Was soll passieren und warum? Mit dem Warum kann der Agent bei Unklarheiten sinnvoll entscheiden.
- **Erfolgskriterien:** Woran erkennt der Agent, dass er fertig ist? Am besten als Akzeptanzkriterien, vor allem für Rand- und Fehlerfälle. Genau die entscheidet ein Agent sonst still selbst.
- **Prüfung:** Wie wird kontrolliert, z. B. „Tests schreiben, `pytest` muss grün sein“? So prüft der Agent sich selbst, bevor er „fertig“ meldet.
- **Grenzen:** Was soll er nicht tun, z. B. keine anderen Funktionen ändern, keine neuen Bibliotheken.

## Was nicht hineingehört

- **Der Lösungsweg.** Wer vorschreibt, *wie* etwas gebaut wird, engt den Agenten unnötig ein (Überspezifikation).
- **Dauerhaftes Projektwissen** wie Architektur, Konventionen oder Testbefehle. Das gehört in die `AGENTS.md`, nicht in jede einzelne Anfrage.

## Wie genau es sein muss

- Abhängig von **Größe und Risiko** der Aufgabe – siehe [Leitfaden](when-to-use-what.md): direkter Prompt, Issue oder Spezifikation.
- Abhängig vom **Modell:** Je kleiner oder schwächer das Modell, desto detaillierter.

## Prüfstein

Würde ein neues Teammitglied die Aufgabe mit dieser Anfrage ohne Rückfragen richtig erledigen? Wenn nicht, fehlt etwas.

## Umsetzung im Kit

- Stufe 2: Issue-Vorlage „Kleine Änderung“ in `.github/ISSUE_TEMPLATE/small-change.md` – Pflicht ist nur das Ziel.
- Stufe 3: `templates/spec.md` und `templates/plan.md`, Ablauf in [spec-workflow.md](spec-workflow.md).
