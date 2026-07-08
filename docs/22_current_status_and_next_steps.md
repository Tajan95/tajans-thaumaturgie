# 22 — Current Status and Next Steps

**Stand:** 2026-07-08, 16:25 Europe/Berlin  
**Status:** Arbeitsübersicht / Orientierungspunkt

Dieses Dokument fasst den aktuellen Arbeitsstand von **Tajan's Thaumaturgie** zusammen und dient als Einstiegspunkt, wenn das Projekt nach einer Pause wieder aufgenommen wird.

Es ersetzt nicht die einzelnen Theorie-, Design- und Simulationsdokumente, sondern verweist auf den aktuellen Fokus.

---

## 1. Kurzstand

Tajan's Thaumaturgie ist inzwischen kein loses Magiekonzept mehr, sondern ein streng material-, energie- und repräsentationsgebundenes Zauber-Programmiersystem.

Aktueller Kern:

```text
Magie = regelgebundene Zustandsmanipulation
        unter Energie-, Massen-, Impuls-, Informations-,
        Präzisions-, Kontroll- und Repräsentationsbedingungen
```

Standardmagie wirkt auf vorhandene Materie und deren Zustände. Ein Zauber ist nur ausführbar, wenn er formal gültig, bezahlbar, simulierbar und physisch-visuell repräsentiert ist.

---

## 2. Aktuell stabile Grundentscheidungen

| ID | Entscheidung | Status |
|---|---|---|
| DD-001 | Projektstruktur wird modular dokumentiert. | Festgelegt |
| DD-002 | Zauber müssen aus kleineren Komponenten ableitbar sein. | Festgelegt |
| DD-003 | Mana ist ein abstrakter Energie-/Arbeitsbegriff, keine konkrete Substanz. | Festgelegt |
| DD-004 | Masse, Energie und Impuls bleiben grundsätzlich erhalten. | Festgelegt |
| DD-005 | LLM/Genie ist Hilfsmittel, nicht Regelautorität. | Festgelegt |
| DD-006 | Makro-Zauber sind Komfortschichten mit emergenter Effizienz. | Festgelegt |
| DD-007 | Zauber benötigen eine physische visuelle Repräsentation. | Festgelegt |
| DD-008 | Zauberbibliotheken verwenden ein Hybridmodell. | Festgelegt |
| DD-009 | Standardmagie ist materiegebunden. | Festgelegt |

Siehe: `docs/07_design_decisions.md`

---

## 3. Die drei großen aktuellen Baustellen

Das Projekt arbeitet aktuell nicht mehr nur an der Klärung der Magie-Theorie/Ontologie. Es hat drei parallele Hauptbaustellen:

| Baustelle | Leitfrage | Relevante Dokumente |
|---|---|---|
| Magie-Theorie und Zaubersystem | Was ist Magie, wie werden Zauber formal konstruiert und begrenzt? | `docs/02_magic_ontology.md`, `docs/03_spell_syntax.md`, `docs/04_modifiers_and_operators.md`, `docs/05_energy_costs_limits.md` |
| Physik und Materialwelt | Wie sieht eine manipulierbare Welt aus, auf die Magie kausal wirken kann? | `docs/15_material_world_model.md`, `docs/16_2d_world_simulation_model.md`, `docs/18_intervention_classes.md`, `docs/20_world_cell_and_chunk_model.md` |
| Technische Implementation | Wie wird daraus ein testbarer 2D-Prototyp mit eigener Simulation? | `docs/19_engine_and_framework_evaluation.md`, `docs/21_material_simulation_benchmark.md`, `prototype/2d/` |

---

## 4. Wichtigster aktueller Arbeitsfokus

Der nächste wirklich sinnvolle Fokus ist nicht mehr „Grundidee formulieren“, sondern:

```text
Von Theorie-Grundsatz → zu minimalem simulierbarem Kern
```

Konkret:

### 1. Zauber-Interne Form entscheiden

Zu klären:

- Sequenz?
- Syntaxbaum?
- Graph?
- Komponentenobjekt?
- Hybrid?

Relevante Issues:

- #2 — Syntaxfrage: Interne Form eines Zaubers bestimmen
- #8 — Feature: Visuelle Zaubersprache und semantische Primitive definieren

---

### 2. Minimalen Prototyp konkretisieren

Zu klären bzw. umzusetzen:

- Weltzellen
- Chunks
- fallender Sand
- Temperatur-Overlay
- lokale Material-/Wärmeeffekte

Relevante Issues:

- #3 — Simulation: Minimalen 2D-Prototyp definieren
- #15 — Prototyp: Minimalen Engine-Benchmark für Materialsimulation definieren
- #19 — Architektur: Simulationskern von Engine-Darstellung trennen
- #21 — Entscheidung: Erste Engine/Framework für Prototyp auswählen
- #23 — Architektur: Datenmodell für Weltzellen und Chunks skizzieren

---

### 3. Zielauswahl formalisieren

Zu klären:

- Punkt
- Radius
- Objekt-ID
- Materialklasse
- Relation
- Sichtlinie
- Bibliotheksdefinition

Relevante Issues:

- #2 — Syntaxfrage: Interne Form eines Zaubers bestimmen
- #10 — Theoriefrage: Zauberbibliotheken, Imports und Referenzen definieren
- #11 — Simulation: Materialwelt, Element- und Stoffkatalog definieren
- #14 — Regelmechanik: Informationsverarbeitende Zauberkomponenten bepreisen

---

### 4. Informationskomponenten begrenzen

Zu klären:

- Suchen
- Filtern
- Sortieren
- Erkennen
- Ausweichen

Leitfrage:

```text
Wie verhindert das System allwissende Analyse-, Such- oder Zielzauber?
```

Relevante Issues:

- #14 — Regelmechanik: Informationsverarbeitende Zauberkomponenten bepreisen
- #10 — Theoriefrage: Zauberbibliotheken, Imports und Referenzen definieren
- #11 — Simulation: Materialwelt, Element- und Stoffkatalog definieren

---

### 5. Physische Zaubersyntax konkretisieren

Zu klären:

- Mindestbestandteile
- Parsermodell
- Glyphen-/Graphenstruktur
- Beschädigung und Fehlerfälle

Relevante Issues:

- #8 — Feature: Visuelle Zaubersprache und semantische Primitive definieren
- #10 — Theoriefrage: Zauberbibliotheken, Imports und Referenzen definieren
- #6 — Begriffsarbeit: Fokusmedien, Zauberstäbe und Artefakte definieren

---

## 5. Nächster sinnvoller Einstieg

Aus aktueller Sicht ist der beste nächste konkrete Arbeitsschritt:

```text
Issue #2 bearbeiten: Interne Form eines Zaubers bestimmen.
```

Begründung:

- Die interne Zauberform beeinflusst Parser, visuelle Sprache, LLM-Compiler, Fehlerdiagnose und Simulation.
- Ohne diese Entscheidung bleiben viele andere Module abstrakt.
- Eine gute Zwischenlösung könnte ein Hybridmodell aus Komponentenobjekt und Wirkungsgraph sein.

Direkt danach sollten Zielauswahl und minimaler 2D-Benchmark weiter konkretisiert werden.

---

## 6. Offener Arbeitsmodus

Bei neuen Notizen weiterhin konsequent unterscheiden:

- **Festgelegt**
- **Hypothese**
- **Offene Frage**
- **Widerspruch**
- **Feature**
- **Begriff**
- **Beispiel**

Neue stabile Entscheidungen gehören in `docs/07_design_decisions.md`.  
Neue offene Theorie- oder Prototypingfragen gehören als GitHub-Issue oder in `docs/06_open_questions.md`.
