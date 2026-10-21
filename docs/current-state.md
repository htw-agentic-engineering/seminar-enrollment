# Current State

<!-- 
  Diese Datei wird nach jedem Merge auf main aktualisiert.
  Wer merged, trägt eine Zeile ein — dauert 30 Sekunden.
  
  Wichtig: Auf einem Feature-Branch wird diese Datei nie bearbeitet.
  Warum? Weil dann bei jedem PR ein Merge-Konflikt entstehen würde,
  wenn mehrere Leute gleichzeitig an verschiedenen Features arbeiten.
  Die Datei lebt nur auf main.
-->

> Vor jeder neuen Aufgabe einmal `git pull origin main` — dann ist dieser Stand aktuell
> und jeder Agent kennt sofort, was die anderen bereits fertiggestellt haben.

## Gemergde Features

| SPEC | Titel | Gemergt am | Branch |
|------|-------|------------|--------|
| — | (noch keine) | — | — |

## Offene Features (noch auf Feature-Branches, noch nicht gemergt)

| Titel | Branch | GitHub Issue |
|-------|--------|--------------|
| — | | |

---

## Drei Regeln für diese Datei

**Regel 1 — Kein manuelles Bearbeiten auf Feature-Branches.**
Nur auf `main` wird diese Datei verändert.

**Regel 2 — Nach jedem Merge eine Zeile eintragen.**
Wer den PR mergt, trägt das Feature oben in die Tabelle ein und entfernt es aus den offenen Features.

**Regel 3 — Vor jeder neuen Aufgabe** `git pull origin main` **ausführen.**
Damit liest der Agent automatisch diesen aktuellen Stand ein und weiß, was alle anderen bereits gebaut haben.
