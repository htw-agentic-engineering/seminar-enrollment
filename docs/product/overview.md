
# Produktüberblick

<!-- Grundlage für alle Spezifikationen. Wird früh im Projekt gemeinsam erarbeitet
     und per Pull Request reviewt. Kein Wort zur Technik. -->

## Vision

**Projektseminar-Verwaltungssystem**

Eine geschützte Webanwendung, über die berechtigte Studierende verfügbare Projektseminare entdecken, deren Beschreibungen lesen und ihre drei priorisierten Themenwünsche einreichen können. Die Plattform schafft Transparenz über den Bewerbungsprozess und gibt Studierenden Sicherheit darüber, dass ihre Angaben übermittelt wurden. Gleichzeitig unterstützt sie Professoren bei der Verwaltung ihrer Seminarangebote und die Administration bei der strukturierten Vergabe der verfügbaren Plätze.

## Rollen

| Rolle | Was sie mit dem System tut |
| --- | --- |
| Studierende | Projektseminare entdecken, PDF-Beschreibungen lesen, Wünsche priorisieren und eine Motivation für den Erstwunsch verfassen. |
| Professoren | Eigene Projektseminare anlegen und verwalten, Beschreibungen bereitstellen sowie verfügbare Plätze angeben. |
| Administration | Zugangsberechtigungen verwalten, Bewerbungen und Motivationsschreiben einsehen, Studierende den Seminaren zuordnen und die Ergebnisse verwalten. |

## Problem Statement

Studierende, die sich für ein Projektseminar bewerben müssen, benötigen einen übersichtlichen und zuverlässigen Prozess, um die angebotenen Themen zu vergleichen und ihre Präferenzen einzureichen. Gleichzeitig benötigt die Administration eine zentrale Übersicht über Bewerbungen, Motivationsschreiben und verfügbare Seminarplätze, um die Vergabe durchführen zu können.

## Personas

<!-- Fiktive, aber typische Nutzer. Die Personas dienen als Arbeitshypothesen
     und können später durch Interviews überprüft werden. -->

### Clara Schmidt

- **Rolle:** Wirtschaftsinformatik-Studentin im 4. Bachelorsemester (Hauptnutzerin)
- **Situation:** Clara muss eines der angebotenen Projektseminare für das kommende Semester auswählen. Es stehen beispielsweise sieben verschiedene Themen zur Verfügung. Sie möchte sich zunächst einen Überblick verschaffen, die PDF-Beschreibungen der Seminare lesen und anschließend die Themen auswählen, die am besten zu ihren Interessen passen. Da die Vergabe über die Plattform erfolgt, möchte sie sicher sein, dass ihre Bewerbung vollständig eingereicht wird.
- **Ziele:**
  - Alle verfügbaren Projektseminare mit Titel, Nummer und betreuendem Professor übersichtlich vergleichen.
  - Die ausführlichen PDF-Beschreibungen einfach öffnen und lesen können.
  - Einen Erst-, Zweit- und Drittwunsch angeben und ihre Motivation für den Erstwunsch formulieren.
  - Eine eindeutige Bestätigung erhalten, dass ihre Bewerbung erfolgreich gespeichert und eingereicht wurde.
  - Ihre eingereichten Wünsche später noch einmal einsehen können.
- **Hindernisse:**
  - Unübersichtliche oder unvollständige Informationen zu den angebotenen Projekten.
  - Unsicherheit darüber, ob die Auswahl und das Motivationsschreiben tatsächlich gespeichert wurden.
  - Unklare Rückmeldungen nach dem Einreichen der Bewerbung.
  - Sorge, durch einen Bedienfehler einen falschen Wunsch abzugeben oder die Bewerbung unvollständig einzureichen.

### Luca Müller

- **Rolle:** Wirtschaftsinformatik-Student im 4. Bachelorsemester (sekundäre Persona)
- **Situation:** Luca arbeitet neben dem Studium als Werkstudent und hat wenig Zeit für organisatorische Aufgaben. Er möchte die Seminarwahl möglichst schnell erledigen, interessiert sich bereits für bestimmte Themen und nutzt häufig sein Smartphone, wenn er unterwegs ist. Er möchte seine drei Wünsche eintragen, ohne sich lange durch die Website navigieren zu müssen.
- **Ziele:**
  - Schnell erkennen, welche Projektseminare angeboten werden und welche Themen für ihn interessant sind.
  - Die wichtigsten Informationen und PDF-Beschreibungen ohne unnötige Zwischenschritte erreichen.
  - Seine drei Wünsche unkompliziert und in der richtigen Reihenfolge eintragen.
  - Die Bewerbung auch auf dem Smartphone problemlos abschließen.
  - Direkt erkennen, ob seine Eingaben gespeichert und die Bewerbung erfolgreich eingereicht wurden.
- **Hindernisse:**
  - Eine komplizierte Navigation oder zu viele unnötige Schritte.
  - Eine schlechte Darstellung auf dem Smartphone.
  - Unklare Kennzeichnungen für Erst-, Zweit- und Drittwunsch.
  - Fehlende Rückmeldungen zum Speicher- oder Einreichungsstatus.
  - Eine unklare Frist oder fehlende Information darüber, ob und bis wann er seine Wünsche noch ändern kann.

### Herr Prof. Wiedemann

- **Rolle:** Professor und Administrator für die Organisation der Projektseminarvergabe
- **Situation:** Herr Prof. Wiedemann koordiniert die Projektseminarvergabe für die berechtigten Studierenden, beispielsweise für Studierende im 4. Bachelorsemester, im 6. Diplomsemester und für Wiederholer. Er muss sicherstellen, dass die verfügbaren Themen und Platzkapazitäten korrekt erfasst sind und die eingegangenen Bewerbungen übersichtlich ausgewertet werden können. Auf Grundlage der Wünsche, der Motivationsschreiben und der verfügbaren Plätze organisiert er die endgültige Zuteilung.
- **Ziele:**
  - Die verfügbaren Projektseminare mit Nummer, Titel, betreuendem Professor, Beschreibung und Platzkapazität zentral verwalten.
  - Sicherstellen, dass ausschließlich berechtigte Studierende Zugang zur Bewerbungsplattform erhalten.
  - Alle eingegangenen Bewerbungen einschließlich Erst-, Zweit- und Drittwunsch sowie der Motivationsschreiben einsehen können.
  - Die Bewerbungen übersichtlich vergleichen und die verfügbaren Plätze bei der Vergabe berücksichtigen.
  - Studierende zuverlässig den jeweiligen Projektseminaren zuordnen und die Ergebnisse verwalten.
  - Den organisatorischen Aufwand reduzieren und Rückfragen zu Anmeldungen und Bewerbungsständen vermeiden.
- **Hindernisse:**
  - Unvollständige, fehlerhafte oder mehrfach eingereichte Bewerbungen.
  - Schwierigkeiten, Bewerbungen und Motivationsschreiben den richtigen Studierenden und Seminarwünschen zuzuordnen.
  - Fehlende Übersicht über die Anzahl der Bewerbungen und die verfügbaren Plätze pro Seminar.
  - Hoher manueller Aufwand bei der Auswertung und Zuteilung.
  - Unklare Berechtigungen oder ungewollte Änderungen an bereits eingereichten Bewerbungen.

## Features

<!-- Grobe Funktionsbereiche, jeweils mit eigenem Feature-Issue
     und später einer Spezifikation in docs/specs/. -->

| Nr. | Feature | Priorität (MoSCoW) | Issue |
| --- | --- | --- | --- |
| 001 | Sichere Anmeldung und Prüfung der Zugangsberechtigung | Must | # |
| 002 | Übersicht der verfügbaren Projektseminare | Must | # |
| 003 | PDF-Beschreibungen der Projektseminare anzeigen | Must | # |
| 004 | Erst-, Zweit- und Drittwunsch auswählen | Must | # |
| 005 | Motivationsschreiben für den Erstwunsch | Must | # |
| 006 | Bewerbung speichern, überprüfen und verbindlich einreichen | Must | # |
| 007 | Bewerbungsstatus und eingereichte Wünsche einsehen | Must | # |
| 008 | Projektseminare und Platzkapazitäten verwalten | Must | # |
| 009 | Bewerbungen einsehen und Studierende zuteilen | Must | # |
| 010 | Änderungen und Ergebnisse der Vergabe verwalten | Should | # |

## Umfang

### Gehört dazu

- Geschützter Zugang für berechtigte Studierende, Professoren und Administratoren.
- Prüfung der Berechtigung anhand der vorgesehenen Studierendengruppen.
- Übersicht aller verfügbaren Projektseminare mit Nummer, betreuendem Professor und Titel.
- Bereitstellung und Anzeige der PDF-Beschreibungen.
- Auswahl und Priorisierung von drei unterschiedlichen Projektseminaren.
- Möglichkeit, eine Motivation für den Erstwunsch zu verfassen.
- Speicherung, Überprüfung und verbindliche Einreichung der Bewerbung.
- Sichtbare Bestätigung und Übersicht der eigenen eingereichten Bewerbung.
- Verwaltung der Projektseminare, Beschreibungen und Platzkapazitäten durch autorisierte Professoren.
- Zentrale Verwaltung und Auswertung der Bewerbungen durch die Administration.
- Manuelle Zuteilung der Studierenden zu den verfügbaren Projektseminaren.
- Verwaltung und Bekanntgabe der endgültigen Zuteilung durch die Administration.

### Gehört ausdrücklich nicht dazu

- Öffentliche Registrierung für beliebige externe Personen.
- Automatische Seminarzuteilung ohne administrative Entscheidung.
- Verwaltung allgemeiner Studienleistungen, Prüfungen oder Noten.
- Vollständige Verwaltung anderer Lehrveranstaltungen außerhalb der vorgesehenen Projektseminare.
- Öffentliches Bewertungs- oder Kommentarsystem für Professoren und Projektseminare.
- Eine eigenständige mobile App; die Anwendung ist als responsive Website vorgesehen.

## Randbedingungen

<!-- Technische, organisatorische oder rechtliche Vorgaben, z. B. Datenschutz, nur Testdaten. -->

- Zugang erhalten ausschließlich die festgelegten berechtigten Studierendengruppen, insbesondere Studierende im 4. Bachelorsemester, im 6. Diplomsemester und zugelassene Wiederholer.
- Die S-Nummer dient als Benutzerkennzeichen und muss durch ein sicheres Authentifizierungsverfahren ergänzt werden.
- Professoren und Administration erhalten unterschiedliche, rollenbasierte Berechtigungen.
- Studierende können nur ihre eigenen Bewerbungen einsehen und bearbeiten, soweit dies innerhalb der festgelegten Fristen erlaubt ist.
- Motivationsschreiben und Bewerbungsdaten dürfen nur für autorisierte Personen zugänglich sein.
- Der Speicher- und Einreichungsstatus muss für Studierende eindeutig erkennbar sein.
- Die endgültige Seminarzuteilung wird durch die Administration vorgenommen.
- Änderungen an Bewerbungen und Seminarangeboten müssen nachvollziehbar bleiben, soweit dies für den ordnungsgemäßen Betrieb erforderlich ist.
- Personenbezogene Daten sind entsprechend den geltenden Datenschutzvorgaben zu verarbeiten.
- Bewerbungsfristen, Änderungsmöglichkeiten, Platzvergabe und Veröffentlichung der Ergebnisse müssen vor der Umsetzung festgelegt werden.
