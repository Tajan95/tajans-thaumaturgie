# Documentation Overview

Dieses Verzeichnis enthält die stabileren Theorie-, System- und Implementationsdokumente von **Tajan's Thaumaturgie**.

Aktive Projektsteuerung liegt bewusst nicht mehr direkt in `docs/`, sondern in `project/` und im Root-Dokument `PROJECT_STATUS.md`.

---

## Einstieg

- `../PROJECT_STATUS.md` — aktueller Projektstand und nächste Schritte
- `../project/design_decisions.md` — getroffene Designentscheidungen
- `../project/open_questions.md` — offene Fragen
- `../project/system_tensions.md` — bekannte Spannungspunkte
- `reference/glossary.md` — Glossar zentraler Begriffe

---

## Struktur

### `foundations/`

Grundannahmen und Projektfundament.

- `project_vision.md`
- `core_principles.md`
- `magic_ontology.md`

### `spell_system/`

Zauberlogik, Syntax, Interventionsklassen, Bibliotheken und Compiler-Fragen.

- `spell_syntax.md`
- `spell_lifecycle_and_activation.md`
- `target_and_effect_node_model.md`
- `modifiers_and_operators.md`
- `intervention_classes.md`
- `spell_libraries_and_references.md`
- `information_processing_spell_components.md`
- `llm_spell_compiler.md`
- `visual_spell_language.md`

### `mana_and_energy/`

Mana, thaumisches Feld, Energiequellen, Kosten, Speicher, Fokusmedien und Artefakte.

- `energy_costs_limits.md`
- `mana_and_thaumic_field_model.md`
- `focus_media_and_artifacts.md`

### `representation_and_material_coupling/`

Physische Zauberrepräsentationen, Materialeinfluss, Grenzflächenmodell und Kopplungsqualität.

- `spell_geometry_and_material_coupling.md`

### `world_model/`

Materialwelt, Weltzellen, Chunks, Mengenauflösung und 2D-Simulationsmodell.

- `material_world_model.md`
- `2d_world_simulation_model.md`
- `world_cell_and_chunk_model.md`
- `world_resolution_and_quantity_model.md`

### `implementation/`

Engine-, Framework-, Benchmark- und Editor-Fragen.

- `engine_and_framework_evaluation.md`
- `material_simulation_benchmark.md`
- `spell_editor_architecture.md`

### `reference/`

Nachschlagewerke.

- `glossary.md`

---

## Prinzip

Neue stabile Theorieinhalte sollen in das jeweils passende Unterverzeichnis überführt werden. Rohnotizen bleiben unter `notes/`, während aktive Entscheidungen und offene Fragen in `project/` gepflegt werden.
