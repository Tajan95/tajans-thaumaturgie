# Tajan's Thaumaturgie

**Stand:** 2026-07-08, 16:25 Europe/Berlin  
**Status:** Frühe Systemarchitektur / Theorie- und Prototypingphase

**Tajan's Thaumaturgie** ist ein Projekt zur Entwicklung eines granularen, modularen und formal ableitbaren Magie-Systems.

Das Ziel ist kein Katalog hardcodierter Zauber, sondern ein regelbasiertes System, in dem Zauber aus kleineren Bedeutungs-, Wirkungs- und Strukturbausteinen zusammengesetzt werden können — ähnlich wie Programme aus Syntax, Operatoren und Datenstrukturen.

Langfristig soll das System digital simulierbar werden: zuerst als 2D-Proof-of-Concept, später optional als ausgereiftere 3D- oder Spielumgebung.

---

## Leitprinzip

> Ein Zauber darf nicht einfach „existieren“, sondern muss aus kleineren, nachvollziehbaren Komponenten logisch ableitbar sein.

---

## Aktueller Kernstand

Das Projekt hat inzwischen mehrere Grundentscheidungen getroffen. Der aktuelle Arbeitsstand lässt sich so zusammenfassen:

```text
Magie = regelgebundene Zustandsmanipulation
        unter Energie-, Massen-, Impuls-, Informations-,
        Präzisions-, Kontroll- und Repräsentationsbedingungen
```

Ein Zauber ist keine freie Realitätsüberschreibung. Er muss formal gültig, bezahlbar, simulierbar und innerhalb der Spielwelt physisch-visuell repräsentiert sein.

Aktuell festgelegt:

- Zauber müssen aus kleineren Komponenten ableitbar sein.
- Mana ist ein abstrakter Energie-/Arbeitsbegriff, keine konkrete Substanz.
- Masse, Energie und Impuls bleiben grundsätzlich erhalten.
- Standardmagie ist materiegebunden und wirkt auf vorhandene Materie bzw. deren Zustände.
- Direkte Feld-/Wellenmagie ist keine Standardmagie, bleibt aber als spätere High-Level-Interventionsklasse offen.
- Jeder ausführbare Zauber benötigt eine physische visuelle Repräsentation, z. B. Schriftrolle, Gravur, Zeichnung, Ritualkreis oder Tattoo.
- Ein LLM/Genie-System kann beim Übersetzen natürlicher Sprache in formale Zauberstruktur helfen, ist aber nicht die Regelautorität.
- Makro-Zauber sind Komfortschichten; ihre Effizienz entsteht emergent aus ihrer Struktur.
- Zauberbibliotheken verwenden ein Hybridmodell aus systemisch verfügbaren Grundprimitiven, memorisierten Makros und lokal/importierten Spezialdefinitionen.

Siehe auch:

- `docs/07_design_decisions.md`
- `docs/22_current_status_and_next_steps.md`

---

## Die drei großen aktuellen Baustellen

Das Projekt arbeitet aktuell parallel an drei Hauptbereichen:

| Baustelle | Leitfrage | Beispiele |
|---|---|---|
| **Magie-Theorie und Zaubersystem** | Was ist Magie, wie werden Zauber formal konstruiert und begrenzt? | Ontologie, Zauber-Syntax, Operatoren, Modifier, Kosten, Fehlerlogik |
| **Physik und Materialwelt** | Wie sieht eine manipulierbare Welt aus, auf die Magie kausal wirken kann? | Materie, Phasen, Temperatur, Materialfraktionen, Erhaltungssätze, Interventionsklassen |
| **Technische Implementation** | Wie wird daraus ein testbarer 2D-Prototyp mit eigener Simulation? | Weltzellen, Chunks, SimulationCore, Rendering, Debug-Overlays, Engine-Benchmark |

---

## Wichtigster aktueller Arbeitsfokus

Der nächste Fokus ist nicht mehr nur „Grundidee formulieren“, sondern:

```text
Von Theorie-Grundsatz → zu minimalem simulierbarem Kern
```

Konkret stehen derzeit diese Aufgaben im Vordergrund:

1. **Zauber-Interne Form entscheiden**  
   Sequenz, Syntaxbaum, Graph, Komponentenobjekt oder Hybridmodell?

2. **Minimalen Prototyp konkretisieren**  
   Weltzellen, Chunks, fallender Sand, Temperatur-Overlay, lokale Material-/Wärmeeffekte.

3. **Zielauswahl formalisieren**  
   Punkt, Radius, Objekt-ID, Materialklasse, Relation, Sichtlinie, Bibliotheksdefinition.

4. **Informationskomponenten begrenzen**  
   Suchen, Filtern, Sortieren, Erkennen, Ausweichen — ohne allwissende Analysezauber zu erlauben.

5. **Physische Zaubersyntax konkretisieren**  
   Mindestbestandteile, Parsermodell, Glyphen-/Graphenstruktur, Beschädigung und Fehlerfälle.

Die ausführlichere Arbeitsübersicht liegt hier:

- `docs/22_current_status_and_next_steps.md`

---

## Projektziele

1. Aufbau einer konsistenten Magie-Ontologie.
2. Entwicklung einer formalen Zauber-Syntax.
3. Definition von Modifiern, Operatoren, Zielauswahl, Dauer, Reichweite und Bedingungen.
4. Modellierung von Energie, Kosten, Grenzen und Fehlerfällen.
5. Entwicklung einer manipulierbaren materiellen Welt als Simulationsgrundlage.
6. Vorbereitung einer digitalen Simulation, zunächst in 2D, später optional in 3D.
7. Prüfung, ob ein LLM-gestützter Zauber-Compiler als Interface zwischen natürlicher Sprache und formaler Zaubersyntax dienen kann.

---

## Arbeitsweise

Das Projekt unterscheidet konsequent zwischen:

- **Theorie:** Was ist im Magie-System grundsätzlich wahr?
- **Regelmechanik:** Wie werden Zauber konstruiert und begrenzt?
- **Simulation:** Wie lässt sich das System technisch abbilden?
- **Gameplay:** Wie wird daraus eine interessante spielbare Erfahrung?
- **Lore:** Wie wird das System innerhalb einer Welt gedeutet?

Neue Ideen werden nach Möglichkeit in diese Kategorien einsortiert:

- **Festgelegt**
- **Hypothese**
- **Offene Frage**
- **Widerspruch**
- **Feature**
- **Begriff**
- **Beispiel**

---

## Projektstruktur

- `docs/` enthält stabile Theorie-, Design- und Architektur-Dokumente.
- `notes/` enthält Rohnotizen und noch nicht bereinigte Gedanken.
- `prototype/` enthält technische Experimente und spätere Prototypen.
- `issues/` enthält Vorlagen und strukturierte Arbeitsaufgaben.

Wichtige Einstiegspunkte:

- `docs/00_project_vision.md` — Projektvision
- `docs/01_core_principles.md` — Grundprinzipien
- `docs/02_magic_ontology.md` — Magie-Ontologie
- `docs/03_spell_syntax.md` — Zauber-Syntax
- `docs/05_energy_costs_limits.md` — Energie, Kosten und Limits
- `docs/07_design_decisions.md` — getroffene Designentscheidungen
- `docs/15_material_world_model.md` — Materialwelt
- `docs/20_world_cell_and_chunk_model.md` — Weltzellen und Chunks
- `docs/21_material_simulation_benchmark.md` — Materialsimulations-Benchmark
- `docs/22_current_status_and_next_steps.md` — aktueller Projektstand und nächste Schritte

---

## Aktueller nächster sinnvoller Einstieg

Aus aktuellem Stand ist der beste nächste konkrete Arbeitsschritt:

```text
Issue #2 bearbeiten: Interne Form eines Zaubers bestimmen.
```

Diese Entscheidung beeinflusst Parser, visuelle Sprache, LLM-Compiler, Fehlerdiagnose und Simulation. Eine plausible Zwischenrichtung ist ein Hybridmodell aus Komponentenobjekt und Wirkungsgraph, muss aber noch sauber ausgearbeitet werden.
