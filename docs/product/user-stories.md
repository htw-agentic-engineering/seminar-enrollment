# User Stories

**Status:** Entwurf, Features noch nicht mit Nataliia (Product Owner) abgestimmt.
**Grundlage:** Personas, Rollen, Feature-Liste und Randbedingungen aus `docs/product/overview.md` (Version aus dem Branch `docs/product-vision`).
**Vorgehen:** Ausgeführt nach dem Skill `.agents/skills/user-story/SKILL.md` (Steps 1–5) mit `template.md`, ins Deutsche übertragen. Mike-Cohn-Format, Akzeptanzkriterien als Gherkin, pro Szenario ein „Wenn“ und ein „Dann“.
**Nicht Teil dieses Dokuments:** Feature 004 (Etienne, siehe Spec 004).

---

## Kontext je Story (Step 1 des Skills)

| Story | Persona | Problem / Ziel laut `overview.md` | Randbedingung |
|---|---|---|---|
| 007-1 | Clara Schmidt | Ziel: „Ihre eingereichten Wünsche später noch einmal einsehen können.“ Hindernis: „Unsicherheit darüber, ob die Auswahl und das Motivationsschreiben tatsächlich gespeichert wurden.“ | Studierende sehen nur ihre eigenen Bewerbungen. Der Speicher- und Einreichungsstatus muss eindeutig erkennbar sein. Fristen noch offen. |
| 002-1 | Luca Müller | Ziel: schnell erkennen, welche Projektseminare es gibt. Hindernisse: „schlechte Darstellung auf dem Smartphone“, „komplizierte Navigation“. | Responsive Website, keine eigene App. Zugang nur für berechtigte Studierende (Feature 001). |
| 008-1 | Prof. Wiedemann | Ziel: Projektseminare mit Nummer, Titel, betreuendem Professor, Beschreibung und Platzkapazität zentral verwalten. Hindernis: „Fehlende Übersicht über … verfügbare Plätze pro Seminar.“ | Rollenbasierte Berechtigungen. Änderungen müssen nachvollziehbar bleiben. |
| 009-1 | Prof. Wiedemann | Ziel: „Alle eingegangenen Bewerbungen einschließlich Erst-, Zweit- und Drittwunsch sowie der Motivationsschreiben einsehen können.“ Hindernis: „Schwierigkeiten, Bewerbungen und Motivationsschreiben den richtigen Studierenden und Seminarwünschen zuzuordnen.“ | Bewerbungsdaten und Motivationsschreiben nur für autorisierte Personen. Rollenbasierte Berechtigungen. |

---

## Feature 007: Bewerbungsstatus und eingereichte Wünsche einsehen

### User Story 007-1

- **Zusammenfassung:** Eingereichte Wünsche einsehen, damit Studierende sicher sind, dass ihre Bewerbung angekommen ist

#### Anwendungsfall
- **Als** Clara Schmidt
- **möchte ich** meine Wünsche, mein Motivationsschreiben und den Status meiner Bewerbung einsehen,
- **damit** ich sicher bin, dass meine Bewerbung vollständig übermittelt wurde, und keine Rückfragen stellen muss.

#### Akzeptanzkriterien

**Szenario 1: Eingereichte Bewerbung ansehen**
- **Angenommen** ich bin angemeldet und als berechtigte Studierende erkannt
- **und angenommen** ich habe meine Bewerbung verbindlich eingereicht
- **Wenn** ich meine Bewerbung öffne
- **Dann** sehe ich den Status „eingereicht“ und meine drei Wünsche mit Nummer und Titel in der Reihenfolge Erst-, Zweit-, Drittwunsch.

**Szenario 2: Motivationsschreiben ansehen**
- **Angenommen** ich bin angemeldet
- **und angenommen** ich habe meine Bewerbung mit einem Motivationsschreiben zum Erstwunsch eingereicht
- **Wenn** ich in meiner Bewerbung das Motivationsschreiben öffne
- **Dann** sehe ich den Text, den ich eingereicht habe.

**Szenario 3: Bewerbung nur gespeichert**
- **Angenommen** ich bin angemeldet
- **und angenommen** ich habe meine Bewerbung gespeichert, aber noch nicht verbindlich eingereicht
- **Wenn** ich meine Bewerbung öffne
- **Dann** sehe ich den Status „noch nicht eingereicht“ und meine gespeicherten Wünsche.

**Szenario 4: Noch keine Bewerbung vorhanden**
- **Angenommen** ich bin angemeldet
- **und angenommen** ich habe noch keine Wünsche gespeichert
- **Wenn** ich meine Bewerbung öffne
- **Dann** erfahre ich, dass noch keine Bewerbung vorliegt.

**Szenario 5: Bewerbung einer anderen Person**
- **Angenommen** ich bin angemeldet
- **und angenommen** eine andere Studierende hat eine Bewerbung eingereicht
- **Wenn** ich versuche, deren Bewerbung zu öffnen
- **Dann** wird mir der Zugriff verweigert.

---

## Feature 002: Übersicht der verfügbaren Projektseminare

### User Story 002-1

- **Zusammenfassung:** Projektseminare auf dem Smartphone überblicken, damit eine Seminarwahl auch unterwegs schnell möglich ist

#### Anwendungsfall
- **Als** Luca Müller
- **möchte ich** auf meinem Smartphone eine übersichtliche Liste aller verfügbaren Projektseminare sehen,
- **damit** ich mit wenig Zeitaufwand erkenne, welche Themen für mich interessant sind.

#### Akzeptanzkriterien

**Szenario 1: Seminarliste auf dem Smartphone**
- **Angenommen** ich bin angemeldet und als berechtigter Studierender erkannt
- **und angenommen** es sind mehrere Projektseminare angelegt
- **und angenommen** ich nutze die Anwendung auf einem Smartphone
- **Wenn** ich die Übersicht der Projektseminare öffne
- **Dann** sehe ich jedes Projektseminar mit Nummer, Titel und betreuendem Professor, ohne seitlich scrollen oder zoomen zu müssen.

**Szenario 2: Übersicht direkt nach der Anmeldung**
- **Angenommen** ich bin berechtigt und gebe meine Zugangsdaten korrekt ein
- **Wenn** ich mich anmelde
- **Dann** sehe ich ohne weitere Zwischenschritte die Übersicht der Projektseminare.

**Szenario 3: Keine Projektseminare vorhanden**
- **Angenommen** ich bin angemeldet
- **und angenommen** es ist noch kein Projektseminar angelegt
- **Wenn** ich die Übersicht der Projektseminare öffne
- **Dann** erfahre ich, dass derzeit keine Projektseminare angeboten werden.

---

## Feature 008: Projektseminare und Platzkapazitäten verwalten

### User Story 008-1

- **Zusammenfassung:** Projektseminare mit Platzkapazität anlegen, damit Studierende korrekte Angebote sehen und die Vergabe planbar wird

#### Anwendungsfall
- **Als** Prof. Wiedemann
- **möchte ich** ein Projektseminar mit Nummer, Titel, betreuendem Professor, PDF-Beschreibung und Platzkapazität anlegen,
- **damit** die Studierenden korrekte Angebote sehen und ich bei der Vergabe weiß, wie viele Plätze je Seminar zur Verfügung stehen.

#### Akzeptanzkriterien

**Szenario 1: Projektseminar anlegen**
- **Angenommen** ich bin als Administrator angemeldet
- **und angenommen** ich habe Nummer, Titel, betreuenden Professor, PDF-Beschreibung und Platzkapazität angegeben
- **Wenn** ich das Projektseminar speichere
- **Dann** erscheint es in der Übersicht der Projektseminare.

**Szenario 2: Pflichtangabe fehlt**
- **Angenommen** ich bin als Administrator angemeldet
- **und angenommen** ich habe den Titel nicht angegeben
- **Wenn** ich das Projektseminar speichere
- **Dann** wird es nicht gespeichert und ich sehe, welche Angabe fehlt.

**Szenario 3: Nummer bereits vergeben**
- **Angenommen** ich bin als Administrator angemeldet
- **und angenommen** es gibt bereits ein Projektseminar mit der Nummer 12
- **Wenn** ich ein weiteres Projektseminar mit der Nummer 12 speichere
- **Dann** wird es nicht gespeichert und ich sehe den Hinweis, dass die Nummer schon vergeben ist.

**Szenario 4: Fehlende Berechtigung**
- **Angenommen** ich bin als Studierende oder Studierender angemeldet
- **Wenn** ich versuche, ein Projektseminar anzulegen
- **Dann** wird mir der Zugriff verweigert.

---

## Feature 009: Bewerbungen einsehen und Studierende zuteilen

Aus Feature 009 ist hier nur der Teil „Bewerbungen einsehen“ umgesetzt. „Bewerbungen je Seminar im Verhältnis zu den Plätzen vergleichen“ und „Studierende einem Seminar zuteilen“ wären eigene Stories (009-2, 009-3).

### User Story 009-1

- **Zusammenfassung:** Eingegangene Bewerbungen einsehen, damit Studierende zuverlässig ihren Wünschen zugeordnet werden können

#### Anwendungsfall
- **Als** Prof. Wiedemann
- **möchte ich** die eingegangenen Bewerbungen mit Erst-, Zweit- und Drittwunsch und den Motivationsschreiben einsehen,
- **damit** ich jede Bewerbung der richtigen Studierenden zuordnen kann und die Zuteilung zu den Projektseminaren vorbereiten kann.

#### Akzeptanzkriterien

**Szenario 1: Übersicht der Bewerbungen**
- **Angenommen** ich bin als Administrator angemeldet
- **und angenommen** mehrere Studierende haben ihre Bewerbung eingereicht
- **Wenn** ich die Übersicht der Bewerbungen öffne
- **Dann** sehe ich zu jeder eingereichten Bewerbung die Studierende oder den Studierenden und den Erstwunsch mit Nummer und Titel.

**Szenario 2: Einzelne Bewerbung ansehen**
- **Angenommen** ich bin als Administrator angemeldet
- **und angenommen** eine Studierende hat ihre Bewerbung eingereicht
- **Wenn** ich ihre Bewerbung öffne
- **Dann** sehe ich, von wem sie stammt, und den Erst-, Zweit- und Drittwunsch mit Nummer und Titel.

**Szenario 3: Motivationsschreiben ansehen**
- **Angenommen** ich bin als Administrator angemeldet
- **und angenommen** eine Studierende hat ihre Bewerbung mit einem Motivationsschreiben zum Erstwunsch eingereicht
- **Wenn** ich in ihrer Bewerbung das Motivationsschreiben öffne
- **Dann** sehe ich den Text, den sie eingereicht hat.

**Szenario 4: Noch keine Bewerbungen**
- **Angenommen** ich bin als Administrator angemeldet
- **und angenommen** es wurde noch keine Bewerbung eingereicht
- **Wenn** ich die Übersicht der Bewerbungen öffne
- **Dann** erfahre ich, dass noch keine Bewerbungen vorliegen.

**Szenario 5: Fehlende Berechtigung**
- **Angenommen** ich bin als Studierende oder Studierender angemeldet
- **Wenn** ich versuche, die Übersicht aller Bewerbungen zu öffnen
- **Dann** wird mir der Zugriff verweigert.

---

## Prüfung nach Step 5 des Skills

| Prüfpunkt | 007-1 | 002-1 | 008-1 | 009-1 |
|---|---|---|---|---|
| „Als“ ist eine benannte Persona, nicht „Nutzer“ | ja | ja | ja | ja |
| „Damit“ nennt ein Ziel und wiederholt nicht das „möchte ich“ | ja | ja | ja | ja |
| Pro Szenario genau ein „Wenn“ und ein „Dann“ | ja (Szenario 1 aufgeteilt) | ja | ja | ja |
| „Dann“ ist prüfbar, nicht vage | ja | ja | ja | ja |
| Keine technische Lösung genannt | ja | ja | ja | ja |
| Zu groß, Aufteilung nötig? | nein | nein | möglicherweise, siehe Frage 4 | bereits aufgeteilt, siehe Frage 9 |

## Offene Fragen

1. **Feature-Zuordnung:** 007, 002 und 008 sind ein Vorschlag und müssen mit Nataliia abgestimmt werden, damit keine Story doppelt entsteht.
2. **Fristen:** `overview.md` sagt, Fristen und Änderbarkeit müssten vor der Umsetzung festgelegt werden. Deshalb steht in 007-1 nichts dazu, ob und bis wann eine eingereichte Bewerbung geändert werden kann.
3. **Eindeutige Seminarnummer (008-1, Szenario 3):** Das ist eine Annahme von uns. In der Vision steht nicht, dass die Nummer eindeutig sein muss.
4. **Umfang von 008:** Die Story bündelt alle Angaben. Anpassen der Platzkapazität, Ändern und Entfernen von Seminaren wären eigene Stories (Skill: „Story zu groß, dann aufteilen“).
5. **Abgrenzung zu Feature 001:** Szenario 2 in 002-1 setzt voraus, dass die Anmeldung funktioniert. Die Anmeldung selbst gehört zu Feature 001.
6. **Glossar:** `docs/product/glossary.md` ist noch leer. Begriffe (Projektseminar, Erstwunsch, Bewerbung, Platzkapazität) stammen aus `overview.md` und müssen ins Glossar übernommen werden.
7. **Gespeicherte Bewerbungen (009-1):** Sieht Prof. Wiedemann auch Bewerbungen, die nur gespeichert, aber nicht verbindlich eingereicht sind? Angenommen sind nur eingereichte.
8. **Mehrfach eingereichte Bewerbungen (009-1):** Als Hindernis genannt, die Vision sagt aber nicht, wie das System damit umgehen soll.
9. **Aufteilung von 009:** „Bewerbungen je Seminar im Verhältnis zu den Plätzen“ (009-2) und „Studierende zuteilen“ (009-3) sind noch nicht geschrieben. Was passiert bei einem vollen Seminar, ist in der Vision nicht geklärt.
10. **Rolle (009-1):** Laut Vision haben „Professoren“ keinen Zugriff auf Bewerbungen. Prof. Wiedemann ist hier als Administrator gemeint.

## KI-Unterstützung

Die Stories wurden mit Claude Code (VS Code) nach dem externen Skill `user-story` von deanpeters geschrieben (`.agents/skills/user-story/`, Quelle und Lizenz siehe `.agents/skills/README.md`). Der Skill ist in Claude Code nicht als Befehl registriert. Er wurde als Textanweisung gelesen und Schritt für Schritt befolgt (Step 1 aus den Personas beantwortet, Step 5 als Tabelle oben). Inhalt, Features und Annahmen wurden von Rico Mauksch geprüft: _(noch eintragen, was übernommen oder verworfen wurde)_.
