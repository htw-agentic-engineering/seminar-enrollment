# Spezifikation: Geräte ausleihen

> **Status:** Freigegeben
> **Feature-Issue:** #4
> **Verantwortlich:** Lena M., Tom K.

<!-- BEISPIEL: So kann eine ausgefüllte Spezifikation aussehen.
     Thema: Ausleihsystem für Laborgeräte einer Hochschule. -->

## Ziel
Studierende sollen Laborgeräte (z. B. Oszilloskope, Messgeräte) selbstständig für Praktika ausleihen können,
ohne dafür zur Sprechzeit des Labors kommen zu müssen. Bisher läuft das über Papierlisten, wodurch Geräte
doppelt vergeben werden und niemand weiß, wer welches Gerät gerade hat.

## Beteiligte
- **Studierende** leihen Geräte aus und geben sie zurück.
- **Laborpersonal** gibt Geräte heraus, nimmt sie zurück und sieht, was verliehen ist.

## Gewünschtes Verhalten
- Als **Studentin** möchte ich sehen, welche Geräte gerade verfügbar sind, damit ich nicht umsonst ins Labor gehe.
- Als **Studentin** möchte ich ein Gerät für einen Zeitraum reservieren, damit es bei der Abholung für mich bereitliegt.
- Als **Laborpersonal** möchte ich sehen, wer welches Gerät bis wann hat, damit ich überfällige Rückgaben erkenne.

## Fachliche Regeln
- **R1:** Ein Gerät kann zu einem Zeitpunkt nur an eine Person verliehen oder für sie reserviert sein.
- **R2:** Eine Ausleihe dauert höchstens 14 Tage.
- **R3:** Eine Person darf höchstens 3 Geräte gleichzeitig ausgeliehen oder reserviert haben.
- **R4:** Eine Reservierung verfällt, wenn das Gerät nicht innerhalb von 2 Werktagen abgeholt wird.
- **R5:** Wer ein Gerät überfällig hat, kann keine neuen Geräte ausleihen.

## Akzeptanzkriterien
- [ ] **AK1** (R1): Angenommen ein Gerät ist reserviert, wenn eine zweite Person es für denselben Zeitraum reservieren will, dann wird das abgelehnt und ein freier Zeitraum vorgeschlagen.
- [ ] **AK2** (R2): Angenommen eine Person wählt einen Zeitraum von mehr als 14 Tagen, dann erscheint ein Hinweis und die Reservierung wird nicht gespeichert.
- [ ] **AK3** (R3): Angenommen eine Person hat bereits 3 Geräte, wenn sie ein weiteres reservieren will, dann wird das abgelehnt.
- [ ] **AK4** (R4): Angenommen eine Reservierung wurde 2 Werktage nicht abgeholt, dann ist das Gerät wieder verfügbar.
- [ ] **AK5** (R5): Angenommen eine Person hat ein überfälliges Gerät, wenn sie ein neues reservieren will, dann wird das abgelehnt und sie wird auf die überfällige Rückgabe hingewiesen.
- [ ] **AK6**: Angenommen ich bin Laborpersonal, wenn ich die Übersicht öffne, dann sehe ich alle verliehenen Geräte mit Person und Rückgabedatum, überfällige zuerst.

## Constraints
- Es werden nur Name und Matrikelnummer gespeichert, keine weiteren personenbezogenen Daten.
- Die Oberfläche muss auf dem Smartphone nutzbar sein.

## Nicht im Umfang
- Mahnungen per E-Mail
- Gebühren oder Strafen bei verspäteter Rückgabe
- Reparatur- und Wartungsplanung der Geräte

## Offene Fragen
- [x] ~~Zählen Wochenenden bei der Abholfrist mit?~~ → nein, siehe E2

## Entscheidungen
| Nr. | Entscheidung | Wer | Datum | Begründung | Verworfene Alternativen |
| --- | --- | --- | --- | --- | --- |
| E1 | Höchstens 3 Geräte pro Person | Team mit Laborleitung | 03.11. | Reicht für alle Praktika, verhindert Horten | 5 Geräte (zu viel bei knappen Geräten) |
| E2 | Abholfrist 2 Werktage, Wochenenden zählen nicht | Team | 05.11. | Labor ist am Wochenende geschlossen | 48 Stunden (Freitagsreservierungen würden verfallen) |
| E3 | Gesperrt wird erst ab überfälliger Rückgabe, nicht schon bei knapper Frist | Team | 05.11. | Einfache, verständliche Regel | Warnung 1 Tag vorher mit Sperre |

## KI-Unterstützung
Die KI hat im Dialog Fragen gestellt und dabei die Randfälle in R4 (verfallene Reservierung) und R5
(Sperre bei Überfälligkeit) eingebracht, die wir vorher nicht bedacht hatten. Ihren Vorschlag einer
automatischen Verlängerung haben wir verworfen, weil die Laborleitung das nicht möchte.
