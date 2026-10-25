# Spezifikation: Erst-, Zweit- und Drittwunsch auswählen

> **Status:** In Review
> **Feature-Issue:** #7
> **Verantwortlich:** Etienne

<!--
Diese Datei beschreibt WAS gebaut wird und WARUM – kein Wort zur Technik.
Das Wie gehört in plan.md.
So detailliert wie nötig, nicht so detailliert wie möglich.
Ändert sich später das Verhalten, wird zuerst diese Datei angepasst, dann der Code.
-->

## Ziel
Studierende müssen ihre Wahlpflichtmodule für das Semester auswählen und priorisieren können. Das System ermöglicht es, genau drei Module auszuwählen und in einer Rangfolge (Platz 1–3) zu speichern. Dies ist die Grundlage für die spätere Modulzuteilung. Für Clara Schmidt (Hauptnutzerin) muss der Vorgang einfach und ohne Fehlerquelle sein — sie will sicher sein, dass ihre Eingabe korrekt gespeichert wurde.

## Beteiligte
- **Clara Schmidt** (Studentin, Hauptnutzerin) – gibt ihre drei Favoriten fristgerecht ab
- **Luca Müller** (Werkstudent, mobil) – gibt die Wahl kurz vor der Frist auf dem Smartphone ab
- **Prof. Wiedemann** (Professor / Modulverantwortlicher) – erhält die eingereichten Prioritäten für die spätere Zuteilung

## Gewünschtes Verhalten
- Als Clara Schmidt möchte ich meine drei Wahlpflichtmodule auswählen und in einer Rangfolge (Platz 1–3) speichern, damit ich fristgerecht meine Präferenzen für die Modulzuteilung einreiche.
- Als Luca Müller möchte ich die Modulwahl auch auf dem Smartphone abgeben können, damit ich sie kurz vor der Frist noch erledigen kann.

## Fachliche Regeln
- **R1:** Jede Studierende muss genau drei Module auswählen.
- **R2:** Die drei Module müssen eindeutig priorisiert sein (Platz 1, Platz 2, Platz 3).
- **R3:** Dasselbe Modul kann nicht mehrfach gewählt werden.
- **R4:** Die Abgabe ist nur innerhalb der Anmeldefrist möglich.
- **R5:** Die Wahl kann bis zum Ende der Anmeldefrist beliebig oft geändert werden.
- **R6:** Eine erneute Abgabe überschreibt die vorherige Wahl vollständig (keine Teilupdates).

## Akzeptanzkriterien
- [ ] **AK1** (R1, R2): Angenommen, eine Studierende öffnet die Modulwahl-Seite, wenn sie drei verschiedene Module auswählt und priorisiert (Platz 1–3), dann wird die Wahl erfolgreich gespeichert und eine Bestätigungsmeldung angezeigt, dass die Eingabe korrekt eingegangen ist.
- [ ] **AK2** (R1): Angenommen, eine Studierende hat nur zwei Module ausgewählt, wenn sie auf "Speichern" klickt, dann wird eine Fehlermeldung angezeigt und die Wahl nicht gespeichert.
- [ ] **AK3** (R3): Angenommen, eine Studierende wählt dasselbe Modul für zwei verschiedene Plätze, wenn sie auf "Speichern" klickt, dann wird eine Fehlermeldung angezeigt.
- [ ] **AK4** (R4): Angenommen, die Anmeldefrist ist abgelaufen, wenn eine Studierende eine Modulwahl abgeben möchte, dann wird dies abgelehnt mit einem Hinweis auf die abgelaufene Frist.
- [ ] **AK5** (R5, R6): Angenommen, eine Studierende hat bereits eine Modulwahl abgegeben, wenn sie eine neue Auswahl trifft und speichert (vor Fristende), dann wird die alte Wahl vollständig durch die neue ersetzt.
- [ ] **AK6** (R2): Angenommen, eine Studierende hat drei Module ausgewählt aber keine Priorisierung vorgenommen, wenn sie auf "Speichern" klickt, dann wird eine Fehlermeldung angezeigt.
- [ ] **AK7** (Story 2): Angenommen, Luca Müller öffnet die Modulwahl-Seite auf einem Smartphone, wenn er drei Module auswählt und priorisiert, dann ist die Oberfläche ohne horizontales Scrollen bedienbar und alle interaktiven Elemente sind mit dem Daumen erreichbar.

## Constraints
- Die Anmeldefrist wird vom Prüfungssekretariat festgelegt und gilt für alle Studierenden verbindlich.
- Die Modulwahl ist eine verbindliche Erklärung – es wird ein Zeitstempel der Abgabe gespeichert.
- **Datenschutz (DSGVO):** Die Modulwahl-Daten der Studierenden dürfen nur für den Zweck der Seminarzuteilung verwendet werden. Testbetrieb nur mit fiktiven Testdaten.

## Nicht im Umfang
- Admin-Ansicht für Prof. Wiedemann (Prioritäten einsehen und exportieren) – das ist Feature 009
- Motivationsschreiben für den Erstwunsch – das ist Feature 005
- Verbindliches Einreichen der Bewerbung – das ist Feature 006
- Bestätigungs-E-Mail an Studierende – On-Screen-Bestätigung ist in AK1 abgedeckt

## Offene Fragen
— keine —

## Entscheidungen
| Nr. | Entscheidung | Wer | Datum | Begründung | Verworfene Alternativen |
| --- | --- | --- | --- | --- | --- |
| E1 | R5: Änderung der Modulwahl bis Fristende erlaubt | Etienne | 25.10.2026 | Luca Müllers Persona nennt explizit „flexibel anpassen" als Ziel; Sperrung nach Abgabe würde jeden Tippfehler zu einer Support-Anfrage machen | R5 ursprünglich: keine Änderung nach Abgabe möglich |
| E2 | Prof. Wiedemanns Admin-Ansicht aus dieser Spec gestrichen | Etienne | 25.10.2026 | Gehört nicht in dieses Feature; separates Feature 009 mit eigenem Issue | Als Story 3 in diese Spec aufgenommen |
| E3 | WCAG 2.1 AA als Constraint gestrichen | Etienne | 25.10.2026 | Niemand im Projekt hat diese Anforderung gestellt; eine Spec-Verpflichtung die nie geprüft wird ist schlechter als keine | Als Constraint C3 im Entwurf enthalten |
| E4 | Seminar-Absage nach Einschreiben: kein Handlungsbedarf | Etienne | 26.10.2026 | Wahrscheinlichkeit < 0,1 %; kein Edge Case der spezifiziert oder implementiert werden muss | Als offene Frage im Entwurf geführt |
| E5 | Weniger als 3 Seminare verfügbar: nicht möglich | Etienne | 26.10.2026 | Das System bietet immer mehr als 3 Seminare an; R1 gilt ohne Ausnahme | Als offene Frage im Entwurf geführt |

## KI-Unterstützung
Skill `spec-writer.md` mit Modell `saia/qwen3.5-397b-a17b` (KISSKI/GWDG via OpenCode CLI) im Dialog ausgeführt. 25.10.2026.

**Übernommen:** Grundstruktur, Ziel-Text (mit manueller Ergänzung zu Clara), AK1–AK6, Constraints Frist + Zeitstempel.

**Korrigiert/verworfen:**
- Beteiligte: „Prüfungsamt" und „Dozierende" ersetzt durch Repo-Personas (Prof. Wiedemann, Luca Müller)
- Story 3 (Prof. Wiedemanns Admin-Ansicht) gestrichen → Scope creep, eigenes Feature
- R5 umgekehrt: Modell schlug Sperre vor, Persona verlangt Flexibilität
- WCAG 2.1 AA Constraint gestrichen: nicht gefordert, leere Verpflichtung
- „konfigurierbar" aus Constraint 1 entfernt: technische Entscheidung, gehört in plan.md

**Ergänzt durch Mensch:** AK7 (Luca mobil), Bestätigungsmeldung in AK1, DSGVO-Constraint, zwei offene Fragen (Modul abgesagt / < 3 Module verfügbar).
