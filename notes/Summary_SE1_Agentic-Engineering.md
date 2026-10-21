# Umfassende Zusammenfassung: Agentic Engineering & Software Engineering 1

Diese Zusammenfassung verknüpft die Prinzipien des "Agentic Engineering" mit den etablierten Grundlagen aus dem Kurs "Software Engineering 1" (SE1). Der Fokus liegt darauf, wie bewährte SE-Methoden essenziell für die erfolgreiche Arbeit mit KI-Coding-Agenten sind.

---

## 1. Kernkonzepte: Agentic Engineering

Agentic Engineering beschreibt einen systematischen Ansatz der Softwareentwicklung, bei dem Aufgaben gezielt an KI-Agenten delegiert werden. Dies steht im Gegensatz zum unstrukturierten "Vibe Coding" (einfach drauflos prompten).

*   **Vibe Coding vs. Agentic Engineering:** Während Vibe Coding explorativ ist und oft zu unwartbarem Code führt, ist Agentic Engineering systematisch, überprüfbar und wartbar. Es basiert auf dem Zyklus: `Spezifizieren -> Delegieren -> Agent Loop -> Verifizieren`.
*   **Die zwei Schleifen der Softwareentwicklung:**
    *   **Innere Schleife (stark beschleunigt durch KI):** Implementieren, Ausführen & Testen, Debugging. Hier arbeiten KI-Agenten extrem schnell.
    *   **Äußere Schleife (der menschliche Flaschenhals):** Spezifizieren & Planen, Überprüfen, Integrieren, Verantwortung übernehmen. Da die KI massenhaft Code erzeugt, wird die menschliche Überprüfung und Planung zur Engstelle.
*   **Aufbau eines Coding-Agenten:** Ein Agent besteht aus einem KI-Modell (dem "Gehirn"), Instruktionen & Kontext, Tools (Dateisystem, Shell, Git), einer Ausführungsumgebung, einem Gedächtnis und dem "Agent Loop", der die Werkzeugaufrufe steuert und Iterationen durchführt.

> 💡 **Relevanz für Agentic Engineering:** 
> Alles ist delegierbar, außer der Verantwortung! Der Mensch muss die äußere Schleife (Planung und Kontrolle) beherrschen, da die KI sonst im "Vibe Coding"-Stil unkontrollierten Output generiert.

---

## 2. SE1-Grundlagen im Kontext von KI-Agenten

Viele aus SE1 bekannte Konzepte sind im Agentic Engineering nicht obsolet, sondern wichtiger denn je, da sie die Kommunikationsbasis mit der KI bilden.

### 2.1 Trennung von Problem- und Lösungsraum

In SE1 wurde gelernt, strikt zwischen dem **Problemraum (Analyse: Was und Warum?)** und dem **Lösungsraum (Entwurf: Wie?)** zu trennen.

*   **Kundenwunsch:** Was der Nutzer grob möchte (z. B. "Einfacher einschreiben").
*   **Anforderung:** Was das System leisten soll, ohne die Lösung vorwegzunehmen.
*   **Technische Lösung:** Wie es umgesetzt wird (Algorithmus, Datenbank).

> 💡 **Relevanz für Agentic Engineering:** 
> Dies ist die häufigste Fehlerquelle beim Prompting! Eine Anforderung darf die Lösung nicht vorwegnehmen. Wer direkt vom Kundenwunsch zur technischen Lösung springt, verwirrt den KI-Agenten oder schränkt dessen Lösungsraum unnötig ein. Die saubere Trennung ist essenziell.

### 2.2 Spec-Driven Development (SDD)

Anstatt dem Agenten zu sagen "Mach Feature X", wird eine explizite Spezifikation (Spec) geschrieben. Die Spezifikation ist die Schnittstelle zwischen der menschlichen Absicht und der KI-Implementierung.

*   **Spezifikation (Was & Warum?):** Enthält Ziel, gewünschtes Verhalten, fachliche Regeln, Akzeptanzkriterien und Constraints.
*   **Plan (Wie?):** Betroffene Komponenten, technische Schritte, Abhängigkeiten.

> 💡 **Relevanz für Agentic Engineering:** 
> SDD ist der Kern des Agentic Engineering. Die Grundregel lautet: Je kleiner oder schwächer das KI-Modell, desto detaillierter muss die Spezifikation (und der Plan) sein. Der Workflow skaliert mit der Größe der Änderung: Kleine Änderungen brauchen nur ein strukturiertes Issue, große Features erfordern umfassendes SDD.

### 2.3 User Stories und Tasks

*   **User Story (Das WAS):** Beschreibt die gewünschte Funktionalität aus Nutzersicht. (z.B. "Als Student will ich...").
*   **Development Task (Das WIE):** Beschreibt die technische Arbeit zur Umsetzung.

Besonders wichtig sind die **3C-Merkmale** von User Stories (Card, Conversation, Confirmation). Die "Confirmation" entspricht den **Akzeptanzkriterien**.

> 💡 **Relevanz für Agentic Engineering:** 
> Akzeptanzkriterien sind für KI-Agenten überlebenswichtig! Sie sagen dem Agenten genau, wann er fertig ist und wann die Umsetzung erfüllt ist. Fehlen sie (Unterspezifikation), füllt die KI Lücken mit falschen Annahmen.

---

## 3. Qualitätsanforderungen und FURPS+

Neben funktionalen Anforderungen gibt es Qualitätsanforderungen und Randbedingungen. In SE1 wird hierfür das FURPS+ Modell genutzt:

*   **F**unctionality (Systemweite Fähigkeiten wie Sicherheit, Auditierung)
*   **U**sability (Gebrauchstauglichkeit, Erlernbarkeit)
*   **R**eliability (Zuverlässigkeit, Verfügbarkeit, Fehlertoleranz)
*   **P**erformance (Antwortzeiten, Durchsatz)
*   **S**upportability (Unterstützbarkeit, Wartbarkeit, Konfigurierbarkeit)
*   **+** Einschränkungen (Constraints wie Vorgaben zu Frameworks, Lizenzen, Datenbanken)

> 💡 **Relevanz für Agentic Engineering:** 
> KI-Agenten neigen dazu, nur die funktionale (Happy-Path) Lösung zu implementieren. Wenn Qualitätsanforderungen (Performance, Sicherheit) oder technische Constraints (z.B. "Nutze nur die bestehende Datenbankstruktur") nicht explizit in der Spezifikation (z. B. in der "Definition of Done") genannt werden, wird die KI sie mit hoher Wahrscheinlichkeit ignorieren.

---

## 4. Technologieauswahl und Wiederverwendung

SE1 unterscheidet klar zwischen Bibliotheken und Frameworks:

*   **Bibliothek (Library):** Wie ein Werkzeugkasten. Der Entwickler (oder die KI) ruft die Funktionen gezielt auf. Der Kontrollfluss bleibt beim Entwickler.
*   **Framework:** Wie ein Baukasten mit Anleitung. Gibt die Architektur vor. Inversion of Control: Das Framework ruft den geschriebenen Code auf.

> 💡 **Relevanz für Agentic Engineering:** 
> KI-Agenten benötigen exakten Kontext über das verwendete Ökosystem, das Framework (z. B. React, Vue, Spring, Django) und den Package Manager. Ohne diese Constraints "erfindet" der Agent möglicherweise eigene, nicht zur Architektur passende Lösungen oder bindet falsche Bibliotheken ein. Ein "Technischer Durchstich" (Spike) hilft, Risiken mit neuen Technologien vorab zu minimieren, bevor man die KI großflächig Code generieren lässt.

---

## 5. Vorgehensmodelle & Agiles Projektmanagement

Projekte werden durch Vorgehensmodelle strukturiert (Wasserfall, V-Modell, Agile wie Scrum).

*   **Scrum-Ablauf:** Product Backlog -> Sprint Planning -> Sprint Backlog -> Daily -> Development -> Review -> Retrospektive.
*   **Definition of Done (DoD):** Kriterien, die erfüllt sein müssen, damit eine Aufgabe als abgeschlossen gilt.

> 💡 **Relevanz für Agentic Engineering:** 
> Die KI muss in den iterativen Prozess (z.B. Scrum) integriert werden. Aufgaben, die dem Agenten übergeben werden, müssen "Ready" sein (Definition of Ready erfüllt). Die KI liefert das Inkrement, das anschließend durch Menschen (und automatisierte Tests) validiert und anhand der DoD geprüft werden muss, bevor es integriert wird.

---

## Zusammenfassendes Fazit für das Agentic Engineering

Die größte Herausforderung beim Einsatz von KI-Coding-Agenten ist nicht das Generieren von Code, sondern das **Spezifizieren, Steuern und Verifizieren**. Ein KI-Agent ist nur so gut wie die Anforderungen, die er erhält. Die in Software Engineering 1 erlernten Techniken – sauberes Requirements Engineering, klare Trennung von Problem/Lösung, detaillierte Akzeptanzkriterien, Berücksichtigung von Nicht-Funktionalen Anforderungen (FURPS+) und solide Architekturplanung – sind das absolute Fundament, um von "Vibe Coding" zu echtem "Agentic Engineering" zu gelangen.
