# Project Status and Next Steps

**Stand:** 2026-07-09, Europe/Berlin  
**Status:** Arbeitsübersicht / Orientierungspunkt

Dieses Dokument fasst den aktuellen Arbeitsstand von **Tajan's Thaumaturgie** zusammen und dient als Einstiegspunkt, wenn das Projekt nach einer Pause wieder aufgenommen wird.

Es ersetzt nicht die einzelnen Theorie-, Design- und Simulationsdokumente, sondern verweist auf den aktuellen Fokus.

---

## 1. Kurzstand

Tajan's Thaumaturgie ist inzwischen kein loses Magiekonzept mehr, sondern ein streng material-, energie-, repräsentations- und kopplungsgebundenes Zauber-Programmiersystem.

Aktueller Kern:

```text
Magie = regelgebundene Zustandsmanipulation
        unter Energie-, Massen-, Impuls-, Informations-,
        Präzisions-, Kontroll-, Repräsentations- und Kopplungsbedingungen
```

Standardmagie wirkt auf vorhandene Materie und deren Zustände. Ein Zauber ist nur ausführbar, wenn er formal gültig, bezahlbar, simulierbar und physisch-visuell repräsentiert ist.

Nach DD-010 ist Mana kein Stoff und kein Teilchen, sondern nutzbarer thaumischer Arbeitsfluss aus realen Energiepotentialen.

```text
physikalisches Energiepotential
→ gekoppeltes thaumisches Potential
→ Zaubergeometrie koppelt daran
→ magische Arbeit
→ physikalische Quelle entlädt sich + Verluste
```

Nach DD-011 kann Zaubergeometrie additiv, subtraktiv oder hybrid realisiert werden. Material und Grenzflächen bestimmen dabei nicht primär die logische Gültigkeit, sondern Kopplungsqualität, Entladerate, Stabilität und Fehlerverhalten.

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
| DD-010 | Mana nutzt ein thaumisches Feldpotential realer Energiequellen. | Festgelegt |
| DD-011 | Zaubergeometrie koppelt material- und grenzflächenabhängig. | Festgelegt |

Siehe: `project/design_decisions.md`

---

## 3. Aktuelle Hauptbaustellen

| Baustelle | Leitfrage | Relevante Dokumente |
|---|---|---|
| Magie-Theorie und Grundsystem | Was ist Magie, wie werden Zauber formal konstruiert und begrenzt? | `docs/foundations/magic_ontology.md`, `docs/spell_system/spell_syntax.md`, `docs/spell_system/modifiers_and_operators.md` |
| Mana, Energie und Kopplung | Was bezahlt magische Arbeit und wie wird sie gespeichert, geleitet und begrenzt? | `docs/mana_and_energy/energy_costs_limits.md`, `docs/mana_and_energy/mana_and_thaumic_field_model.md`, `docs/mana_and_energy/focus_media_and_artifacts.md` |
| Physische Repräsentation | Wie wirken Zauberbilder als reale Kopplungsstrukturen? | `docs/spell_system/visual_spell_language.md`, `docs/representation_and_material_coupling/spell_geometry_and_material_coupling.md` |
| Physik und Materialwelt | Wie sieht eine manipulierbare Welt aus, auf die Magie kausal wirken kann? | `docs/world_model/material_world_model.md`, `docs/world_model/2d_world_simulation_model.md`, `docs/world_model/world_cell_and_chunk_model.md` |
| Technische Implementation | Wie wird daraus ein testbarer 2D-Prototyp mit eigener Simulation? | `docs/implementation/engine_and_framework_evaluation.md`, `docs/implementation/material_simulation_benchmark.md`, `prototype/2d/` |

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

Relevante Dokumente:

- `docs/spell_system/spell_syntax.md`
- `docs/spell_system/visual_spell_language.md`
- `docs/spell_system/llm_spell_compiler.md`

---

### 2. Minimalen Prototyp konkretisieren

Zu klären bzw. umzusetzen:

- Weltzellen
- Chunks
- fallender Sand
- Temperatur-Overlay
- lokale Material-/Wärmeeffekte
- erste thaumische Zustandswerte für Speicher und Quellen

Relevante Dokumente:

- `docs/world_model/2d_world_simulation_model.md`
- `docs/world_model/world_cell_and_chunk_model.md`
- `docs/implementation/material_simulation_benchmark.md`

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

Relevante Dokumente:

- `docs/spell_system/spell_syntax.md`
- `docs/spell_system/spell_libraries_and_references.md`
- `docs/world_model/material_world_model.md`

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

Relevante Dokumente:

- `docs/spell_system/information_processing_spell_components.md`
- `project/open_questions.md`

---

### 5. Physische Zaubersyntax konkretisieren

Zu klären:

- Mindestbestandteile
- Parsermodell
- Glyphen-/Graphenstruktur
- Beschädigung und Fehlerfälle
- Kopplungswirkung der Geometrie nach DD-010 und DD-011

Relevante Dokumente:

- `docs/spell_system/visual_spell_language.md`
- `docs/representation_and_material_coupling/spell_geometry_and_material_coupling.md`
- `docs/mana_and_energy/mana_and_thaumic_field_model.md`

---

### 6. Thaumische Material- und Speicherwerte konkretisieren

Zu klären:

- `mana_capacity`
- `mana_charge`
- `thaumic_potential`
- `mana_conductivity`
- `mana_leakage`
- `mana_conversion_efficiency`
- `mana_discharge_rate`
- `mana_overload_threshold`

Leitfrage:

```text
Welche Mana-relevanten Materialattribute sind für den ersten Prototyp wirklich nötig?
```

Relevante Dokumente:

- `docs/mana_and_energy/energy_costs_limits.md`
- `docs/mana_and_energy/focus_media_and_artifacts.md`
- `docs/mana_and_energy/mana_and_thaumic_field_model.md`
- `docs/representation_and_material_coupling/spell_geometry_and_material_coupling.md`
- `project/open_questions.md` OQ-025 bis OQ-027

---

## 5. Nächster sinnvoller Einstieg

Aus aktueller Sicht ist der beste nächste konkrete Arbeitsschritt weiterhin:

```text
Issue #2 bearbeiten: Interne Form eines Zaubers bestimmen.
```

Begründung:

- Die interne Zauberform beeinflusst Parser, visuelle Sprache, LLM-Compiler, Fehlerdiagnose und Simulation.
- Ohne diese Entscheidung bleiben viele andere Module abstrakt.
- Eine gute Zwischenlösung könnte ein Hybridmodell aus Komponentenobjekt und Wirkungsgraph sein.
- Nach DD-010 und DD-011 muss die interne Form später auch Energiequelle, thaumischen Fluss, Kopplungsgeometrie, Materialkopplung und Zielzustand sauber abbilden können.

Direkt danach sollten Zielauswahl, minimaler 2D-Benchmark und die ersten thaumischen Materialwerte weiter konkretisiert werden.

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

Neue stabile Entscheidungen gehören in `project/design_decisions.md`.  
Neue offene Theorie- oder Prototypingfragen gehören in `project/open_questions.md` oder als GitHub-Issue.
