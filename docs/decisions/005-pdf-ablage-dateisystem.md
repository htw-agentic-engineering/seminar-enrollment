# ADR-005: PDF-Seminarbeschreibungen im Dateisystem hinter einer Schnittstelle

> **Status:** Vorgeschlagen
> **Datum:** 23.11.2026
> **Beteiligt:** Rico Mauksch

## Kontext
Professoren bzw. die Administration laden für jedes Projektseminar eine Seminarbeschreibung als PDF hoch
(#29); Studierende öffnen sie in der Seminarübersicht (#24). Die Anwendung ist nur für angemeldete Nutzer
zugänglich. Es geht um wenige Dutzend PDFs pro Semester. Die Anwendung läuft zunächst lokal; ein Hosting
ist noch nicht festgelegt.

## Entscheidung
Die PDF-Dateien werden im **Dateisystem** in einem Upload-Ordner gespeichert. In der Datenbank stehen nur
die Metadaten (Zuordnung zum Projektseminar, Dateiname, Größe, Upload-Datum).

Der Zugriff liegt **hinter einer Schnittstelle** (`DocumentStorage` in `src/application/`: speichern, laden,
löschen), umgesetzt durch `FileSystemDocumentStorage` in `src/infrastructure/`.

## Alternativen
| Alternative | Vorteile | Nachteile | Warum nicht |
| --- | --- | --- | --- |
| In PostgreSQL als Binärdaten | Alles an einem Ort, ein Backup | Datenbank wird groß und langsamer; unüblich | Kein Vorteil bei dieser Menge |
| Objektspeicher (S3/MinIO) | Skalierbar, Cloud-Standard | Zusätzlicher Dienst muss laufen | Für die Menge an PDFs übertrieben |

## Konsequenzen
- Positiv: Einfach, kein zusätzlicher Dienst; Dateien sind direkt einsehbar.
- Positiv: Ein späterer Wechsel zu einem Objektspeicher betrifft nur einen Adapter in `src/infrastructure/`.
- Negativ: Funktioniert nicht auf Serverless-Hosting (z. B. Vercel). Ein späterer Betrieb braucht einen eigenen Server oder Container mit dauerhaftem Speicher.
- Negativ: Der Upload-Ordner muss beim Backup zusätzlich zur Datenbank gesichert werden.
- Zu beachten: PDFs liegen **nicht** im `public/`-Ordner von Next.js, sonst wären sie ohne Anmeldung abrufbar. Sie werden über eine Route ausgeliefert, die vorher die Anmeldung prüft.
- Zu beachten: Beim Upload wird geprüft, dass es sich wirklich um ein PDF handelt (Dateiinhalt, nicht nur Endung) und eine Höchstgröße eingehalten wird. Den Wert legt die Spezifikation fest.
- Zu beachten: Der Upload-Ordner gehört nicht ins Git-Repository.

## KI-Unterstützung
Die KI hat drei Ablageorte verglichen, das Dateisystem hinter einer Schnittstelle empfohlen und auf den
geschützten Abruf und die Upload-Prüfung hingewiesen. Das Team ist der Empfehlung gefolgt.
