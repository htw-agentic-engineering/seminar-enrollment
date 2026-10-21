# Plan: Geräte ausleihen

> **Spezifikation:** [spec.md](spec.md)
> **Status:** Freigegeben

<!-- BEISPIEL: So kann ein ausgefüllter Plan zur Beispiel-Spezifikation aussehen. -->

## Ansatz
Ausleihe und Reservierung werden als ein Domänenobjekt `Loan` mit Status (reserviert, ausgeliehen,
zurückgegeben, verfallen) abgebildet. Alle fachlichen Regeln (R1–R5) liegen in der Domain-Schicht,
damit sie unabhängig von Datenbank und Oberfläche getestet werden können.
Der Verfall von Reservierungen (R4) wird beim Abruf geprüft, nicht über einen zeitgesteuerten Job –
das ist einfacher und reicht für die erwartete Nutzung.

## Betroffene Teile
- `src/domain/loan.py` – neu: Loan, Regeln R1–R5
- `src/domain/device.py` – erweitert: Verfügbarkeit
- `src/application/reserve_device.py` – neu: Ablauf „Gerät reservieren“
- `src/application/loan_overview.py` – neu: Übersicht für Laborpersonal
- `src/infrastructure/loan_repository.py` – neu: Speichern und Laden von Ausleihen
- `src/presentation/` – Seiten „Geräte“ und „Übersicht“

## Aufgaben
| Nr. | Aufgabe | Deckt ab | Abhängig von | Issue |
| --- | --- | --- | --- | --- |
| T1 | Domänenobjekt `Loan` mit Status und Regeln R1–R3, R5 | AK1, AK2, AK3, AK5 | – | #11 |
| T2 | Verfall von Reservierungen nach 2 Werktagen | AK4 | T1 | #12 |
| T3 | Repository für Ausleihen | – | T1 | #13 |
| T4 | Ablauf „Gerät reservieren“ inkl. Vorschlag eines freien Zeitraums | AK1–AK5 | T1, T3 | #14 |
| T5 | Übersicht für Laborpersonal, überfällige zuerst | AK6 | T3 | #15 |
| T6 | Oberfläche: Geräteliste und Reservierungsformular | AK1–AK3 | T4 | #16 |

## Teststrategie
- **Domain (T1, T2):** Unit-Tests für jede Regel R1–R5. Die Tests zu R1 und R4 schreibt ein Mensch selbst,
  weil Doppelbelegung und Fristberechnung die fehleranfälligsten Stellen sind.
- **Application (T4, T5):** Tests für jedes Akzeptanzkriterium mit einem In-Memory-Repository.
- **Oberfläche (T6):** manuelle Prüfung auf dem Smartphone.

## Risiken und offene technische Fragen
- Werktage-Berechnung: Feiertage werden zunächst ignoriert. Falls nötig, später als eigene Aufgabe.
- Gleichzeitige Reservierung desselben Geräts durch zwei Personen: wird über eine Prüfung beim Speichern abgefangen (T3).
