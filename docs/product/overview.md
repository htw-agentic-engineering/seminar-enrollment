
# Produktüberblick

<!-- Grundlage für alle Spezifikationen. Wird früh im Projekt gemeinsam erarbeitet
     und per Pull Request reviewt. Kein Wort zur Technik. -->

## Vision

**Projektseminar-Verwaltungssystem**

Eine geschützte Webanwendung, über die berechtigte Studierende verfügbare Projektseminare entdecken, deren Beschreibungen lesen und ihre drei priorisierten Themenwünsche einreichen können. Die Plattform schafft Transparenz über den Bewerbungsprozess und gibt Studierenden Sicherheit darüber, dass ihre Angaben übermittelt wurden. Gleichzeitig unterstützt sie Professoren bei der Verwaltung ihrer Seminarangebote und die Administration bei der strukturierten Vergabe der verfügbaren Plätze.

**Motivation**

Die bisherige Organisation der Projektseminare erfolgte über OPAL. Dabei konnten sich Studierende ab einem festgelegten Zeitpunkt für die Seminare anmelden. Bei besonders gefragten Seminaren hatten häufig diejenigen einen Vorteil, die über eine schnellere Internetverbindung verfügten und sich früher anmelden konnten. Dadurch entstand der Wunsch nach einem faireren Verfahren, bei dem nicht die Geschwindigkeit der Anmeldung, sondern die fachliche Eignung und die Interessen der Studierenden stärker berücksichtigt werden.

Die neue Anwendung soll diesen Prozess verbessern. Studierende können sich über die angebotenen Projektseminare informieren und mehrere Wünsche in einer festgelegten Reihenfolge angeben. Zusätzlich können sie ihre Motivation für den Erstwunsch erläutern. Bei der späteren Verteilung sollen neben den verfügbaren Plätzen insbesondere die fachlichen Interessen, Begründungen und gegebenenfalls vorhandene Berufs- und Praxiserfahrungen der Studierenden berücksichtigt werden.

Ein weiteres Ziel ist es, den organisatorischen Aufwand für den Studiendekan und die beteiligten Professoren zu reduzieren. Durch die Anwendung sollen ausgewählte administrative Aufgaben unterstützt und teilweise automatisiert werden. Dazu könnte beispielsweise die Auswertung der eingereichten Wünsche und die Erstellung von Vorschlägen für eine möglichst passende Verteilung gehören. Die endgültige Entscheidung über die Zuordnung soll weiterhin von den verantwortlichen Personen getroffen werden.

## Rollen

| Rolle | Was sie mit dem System tut |
| --- | --- |
| Studierende | Projektseminare entdecken, PDF-Beschreibungen lesen, Wünsche priorisieren und eine Motivation für den Erstwunsch verfassen. |
| Professoren | Projektseminarthemen, Beschreibungen (PDF-Dateien) und verfügbare Plätze an die Administration übermitteln. Bei Bedarf die eingegangenen Wünsche einsehen und an der Zuordnung der Studierenden mitwirken. |
| Administration (Studiendekan) | Zugangsberechtigungen verwalten, Seminarangebote und Beschreibungen einpflegen, Bewerbungen und Motivationsschreiben einsehen, Studierende unter Berücksichtigung ihrer Wünsche und fachlichen Interessen den Seminaren zuordnen sowie die Ergebnisse verwalten und veröffentlichen. |

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
| 001 | Sichere Anmeldung und Prüfung der Zugangsberechtigung | Must | #22 |
| 002 | Übersicht der verfügbaren Projektseminare | Must | #23 |
| 003 | PDF-Beschreibungen der Projektseminare anzeigen | Must | #24 |
| 004 | Erst-, Zweit- und Drittwunsch auswählen | Must | #25 |
| 005 | Motivationsschreiben für den Erstwunsch | Must | #26 |
| 006 | Bewerbung speichern, überprüfen und verbindlich einreichen | Must | #27 |
| 007 | Bewerbungsstatus und eingereichte Wünsche einsehen | Must | #28 |
| 008 | Projektseminare und Platzkapazitäten verwalten | Must | #29 |
| 009 | Bewerbungen einsehen und Studierende zuteilen | Must | #30 |
| 010 | Änderungen und Ergebnisse der Vergabe verwalten | Should | #31 |
| 011 | Bewerbung bis zum Ablauf der Bewerbungsfrist bearbeiten | Should | #33 |
| 012 | Bewerbungen nach Projektseminar filtern und sortieren | Should | #34 |
| 013 | Anzahl der Bewerbungen und Nachfrage pro Projektseminar anzeigen | Should | #35 |
| 014 | Bewerbungsfrist verwalten und Bewerbungsphase abschließen | Should | #36 |
| 015 | Bewerbungen mithilfe von KI anhand definierter Kriterien auswerten | Could | #38 (Epic #37) |
| 016 | Kapazitäts- und wunschbasierte Zuteilungsvorschläge erstellen | Could | #39 (Epic #37) |
| 017 | Administrative Übersicht für Bewerbungsanalyse und Zuteilungsvorschläge | Could | #40 (Epic #37) |

## Anmeldung und Zugangsberechtigung

Der Zugang zur Anwendung ist auf berechtigte Studierende beschränkt. Die Anmeldung erfolgt über das LDAP-System der Fakultät. Dabei wird überprüft, ob die eingegebenen Zugangsdaten gültig sind und die Person zur Nutzung der Anwendung berechtigt ist. Ist die Authentifizierung nicht erfolgreich, wird der Zugriff verweigert.

Nur zugelassene Studierendengruppen können ihre Projektseminarwünsche einreichen. Welche Studiengänge und Fachsemester konkret zugelassen sind, muss noch abschließend geklärt werden.

## Kriterien für die Zuordnung der Studierenden

Die Zuordnung der Studierenden zu den Projektseminaren erfolgt durch die Administration (Studiendekan). Dabei werden nicht nur die drei priorisierten Themenwünsche berücksichtigt, sondern auch die fachliche Eignung und die individuelle Motivation der Studierenden.

Bei der Bewertung können unter anderem folgende Kriterien berücksichtigt werden:

- **Priorisierung der Wünsche:** Erst-, Zweit- und Drittwunsch der Studierenden.
- **Motivationsschreiben:** Qualität und fachlicher Bezug der Begründung für den Erstwunsch.
- **Berufserfahrung:** Bereits vorhandene Berufserfahrungen, die zum jeweiligen Projektseminar passen.
- **Berufsinteressen:** Bestehende berufliche Interessen und angestrebte Tätigkeitsbereiche.
- **Fachlicher Bezug:** Übereinstimmung der bisherigen Erfahrungen und Interessen mit den Inhalten des jeweiligen Projektseminars.
- **Verfügbare Plätze:** Anzahl der Plätze, die in den einzelnen Projektseminaren zur Verfügung stehen.

Besonders passende Berufserfahrungen und fachliche Interessen können bei der Zuordnung positiv bewertet werden. Studierende mit einer nachvollziehbaren Motivation und einem erkennbaren fachlichen Interesse werden bevorzugt berücksichtigt. Weniger aussagekräftige Begründungen oder ein kaum erkennbares fachliches Interesse können zu einer niedrigeren Priorisierung führen.

Ziel ist eine möglichst faire Verteilung, bei der sowohl die Wünsche der Studierenden als auch die fachliche Passung und die verfügbaren Kapazitäten berücksichtigt werden.

## Potenzial zur Unterstützung durch KI-Agenten

Die Bewertung und Zuordnung der Studierenden zu den Projektseminaren ist mit einem erheblichen organisatorischen Aufwand verbunden. KI-Agenten könnten diesen Prozess unterstützen, indem sie die eingereichten Bewerbungen analysieren und anhand festgelegter Kriterien bewerten.

Mögliche Aufgaben der KI-Agenten:

- Auswertung der Motivationsschreiben hinsichtlich des fachlichen Bezugs zum jeweiligen Seminar.
- Erkennung relevanter Berufserfahrungen und beruflicher Interessen.
- Abgleich der Qualifikationen und Interessen der Studierenden mit den Inhalten der Projektseminare.
- Berücksichtigung der priorisierten Seminarwünsche.
- Erstellung von Bewertungsvorschlägen anhand definierter Kriterien.
- Vorschläge für eine möglichst passende Verteilung unter Berücksichtigung der verfügbaren Plätze.

Die KI soll dabei keine endgültigen Entscheidungen treffen, sondern die Administration durch strukturierte Bewertungen und Zuordnungsvorschläge unterstützen. Die finale Entscheidung über die Verteilung bleibt beim Studiendekan.
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
