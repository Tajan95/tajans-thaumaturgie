# Project Status and Next Steps

**Stand:** 2026-07-14, 01:44 Europe/Berlin  
**Status:** Arbeitsübersicht / Orientierungspunkt

Dieses Dokument fasst den aktuellen Arbeitsstand von **Tajan's Thaumaturgie** zusammen und dient als Einstiegspunkt, wenn das Projekt nach einer Pause wieder aufgenommen wird.

Es ersetzt nicht die einzelnen Theorie-, Design- und Simulationsdokumente, sondern verweist auf den aktuellen Fokus.

---

## 1. Kurzstand

Tajan's Thaumaturgie ist inzwischen ein streng material-, energie-, repräsentations- und kopplungsgebundenes Zauber-Programmiersystem.

```text
Magie = regelgebundene Zustandsmanipulation
        unter Energie-, Massen-, Impuls-, Informations-,
        Präzisions-, Kontroll-, Repräsentations- und Kopplungsbedingungen
```

Standardmagie wirkt auf vorhandene Materie und deren Zustände. Ein Zauber ist nur ausführbar, wenn er formal gültig, bezahlbar, simulierbar und physisch-visuell repräsentiert ist.

Aktueller thaumischer Energiepfad:

```text
physikalisches Energiepotential
→ gekoppeltes thaumisches Potential
→ Zaubergeometrie koppelt daran
→ magische Arbeit
→ physikalische Quelle entlädt sich + Verluste
```

Der aktuelle Syntaxkern entwickelt sich zu:

```text
Interne Zauberform
= Komponentenobjekt
+ typisierter gerichteter Wirkungsgraph
```

Bereits konkretisiert:

```text
ActivationNode
→ TargetNode(s)
→ EffectNode(s)
→ StateChangeRequest(s)
→ Validierung und Simulation
```

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
| DD-012 | Zauber besitzen eine Start-Glyphe mit Default-Sofortausführung. | Festgelegt |
| DD-013 | TargetNodes erzeugen explizite typisierte Zielmengen. | Festgelegt |
| DD-014 | Primitive EffectNodes enthalten eine atomare Zustandsoperation. | Festgelegt |
| DD-015 | Zauberlogik verbraucht eigene thaumische Steuerarbeit. | Festgelegt |
| DD-016 | WorldCells sind räumliche Einheiten, keine Mindestmassen. | Festgelegt |
| DD-017 | Der erste Prototyp verwendet eine 2D-Seitenansicht. | Festgelegt |
| DD-018 | Starre Objekte und Flussmaterialien verwenden unterschiedliche Bewegungsmodelle. | Festgelegt |
| DD-019 | Physikalische Größen bleiben SI-kompatibel und numerisch quantisierbar. | Festgelegt |

Siehe: `project/design_decisions.md`

---

## 3. Aktuelle Hauptbaustellen

| Baustelle | Leitfrage | Relevante Dokumente |
|---|---|---|
| Magie-Theorie und Grundsystem | Was ist Magie und wie werden Zauber formal konstruiert? | `docs/foundations/magic_ontology.md`, `docs/spell_system/spell_syntax.md` |
| Zauberlebenszyklus | Wie starten, laufen und enden Zauber? | `docs/spell_system/spell_lifecycle_and_activation.md` |
| Ziel- und Wirkungsmodell | Wie werden Ziele gebunden und atomare Zustandsänderungen angefordert? | `docs/spell_system/target_and_effect_node_model.md` |
| Mana, Energie und Kopplung | Was bezahlt magische Arbeit und wie wird sie geleitet? | `docs/mana_and_energy/energy_costs_limits.md`, `docs/mana_and_energy/mana_and_thaumic_field_model.md` |
| Physische Repräsentation | Wie wirken Zauberbilder als reale Kopplungsstrukturen? | `docs/spell_system/visual_spell_language.md`, `docs/representation_and_material_coupling/spell_geometry_and_material_coupling.md` |
| Physik und Materialwelt | Wie sieht eine manipulierbare, quantisierte Welt aus? | `docs/world_model/material_world_model.md`, `docs/world_model/world_resolution_and_quantity_model.md` |
| Technische Implementation | Wie wird daraus ein testbarer 2D-Prototyp und Spell Editor? | `docs/implementation/material_simulation_benchmark.md`, `docs/implementation/spell_editor_architecture.md` |

---

## 4. Issue #2 — Interne Form eines Zaubers

**Status:** Deutlich teilweise geklärt.

### 4.1 Aktivierung und Beendigung

Geklärt:

- Jeder ausführbare Zauber besitzt mindestens einen ActivationNode bzw. eine Start-Glyphe.
- Ohne expliziten Start-Modifier gilt `on_complete_execute_once`.
- Verzögerung, Vokalisierung, Gestik, Umweltbedingungen, Halten, Toggle, Dauerlimit, autonomer Quellenlauf, Wiederholung und Failsafes sind explizite syntaktische Bestandteile.

### 4.2 Zielauswahl

Geklärt:

```text
TargetNode → TargetSet
```

TargetNodes definieren mindestens:

- Selektor
- Anker
- Suchraum
- Filter
- Granularität
- Bindungsmodus
- Aktualisierung
- Zugriffsvoraussetzungen
- Fehlerverhalten

Mögliche Referenzen:

```text
ObjectRef
CellRef
CellRegionRef
SurfaceRef
MaterialFractionRef
PointRef
BiologicalRegionRef
```

Bindungsmodi:

```text
snapshot
live
```

Live-Bindung verursacht zusätzliche Such-, Bindungs- und Steuerkosten.

### 4.3 Wirkungen

Geklärt:

- Ein primitiver EffectNode enthält genau eine atomare Zustandsoperation.
- Mehrere Effekte werden durch parallele oder sequenzielle Graphzweige kombiniert.
- Makros dürfen Teilgraphen kompakt darstellen, werden für Kosten und Prüfung aber expandiert.
- Physikalisch gekoppelte Gegenänderungen dürfen Teil derselben Transferoperation sein.

Vorläufige Effect-Domänen:

- mechanisch-kinematisch
- mechanisch-strukturell
- thermisch
- elektrisch in Materie
- kompositionell / transportbezogen
- chemisch
- phasenbezogen
- nuklear

Informationsoperationen werden als Query-/Analysis-Nodes modelliert. Biologische und kognitive Zauber sind keine elementaren Standardprimitive, sondern komplexe Makros über materiellen und informationsbezogenen Operationen.

### 4.4 StateChangeRequest

```text
EffectNode
→ StateChangeRequest
→ Regel-, Kosten- und Erhaltungsprüfung
→ SimulationCore
```

Der EffectNode verändert die Welt nicht unmittelbar. Er fordert eine prüfbare Zustandsänderung an.

### 4.5 Kosten

```text
Gesamtarbeit =
    physikalische Effektarbeit
  + Zielerfassung und Zielbindung
  + Steuer- und Präzisionsarbeit
  + Kopplungsverluste
  + Sicherheits- und Prüfoperationen
  + kontinuierliche Laufzeitkosten
  + Nebenproduktbehandlung
```

Kosten richten sich nach dem expandierten internen Graphen, nicht nach der sichtbaren Zahl der Editor-Knoten.

---

## 5. Welt- und Simulationsmodell

### 5.1 Grundansicht

Der erste Prototyp verwendet eine 2D-Seitenansicht.

Optional:

```text
Hintergrund
Hauptebene
Vordergrund
```

als diskrete Tiefenebenen, nicht als kontinuierliche 3D-Achse.

### 5.2 Getrennte Auflösungen

```text
WorldCell-Größe
≠ Mindestmasse
≠ Mindeststoffanteil
≠ Mindestenergie
≠ Positionsauflösung
```

Sub-Zell-Massen und Stofffraktionen bleiben erhalten. Ein Spurengas kann innerhalb einer Luftzelle existieren und über mehrere Zellen akkumuliert werden, ohne vorher ein sichtbares Pixel zu bilden.

### 5.3 Bewegungsmodell

```text
starre Objekte:
Sub-Zell-Position + kontinuierliche Geschwindigkeit + rasterisierte Belegung

Granulate / Flüssigkeiten / Gase:
zellbasierter Massen-, Impuls- und Energietransfer
```

### 5.4 Numerische Einheiten

Semantische Größen bleiben SI-kompatibel.

Bevorzugte Arbeits- und Anzeigeeinheiten:

- Meter
- Gramm
- Sekunde
- Kelvin
- Joule
- Newton
- Watt

Starke Implementationshypothese:

```text
Fixed-Point-Integer
+ interne Energiequanten kleiner als 1 J
+ erster Benchmark mit Millijoule
```

### 5.5 Kompositionsspeicherung

Empfohlene technische Richtung:

```text
kleiner Inline-Komponentenspeicher
+ externer CompositionPool
+ Copy-on-Write für häufige Gemische
```

Es gibt kein semantisches Stofflimit pro Zelle. Die konkrete schnelle Inline-Kapazität, z. B. vier oder acht Komponenten, bleibt eine Benchmarkentscheidung.

---

## 6. Spell Editor

Der Spell Editor bleibt ein früher Prototypkandidat und verbindet:

- visuelle Graph-/Glyphenfläche
- textuelle Code-/IDE-Syntax
- Genie-Fenster für natürliche Sprache

```text
Visual Canvas ↔ SpellIR ↔ Code Editor
                  ↑
                  |
             Genie Draft
```

Die neuen TargetNode-, EffectNode- und StateChangeRequest-Verträge liefern erste konkrete Typen für `SpellIR`.

Relevantes Dokument:

- `docs/implementation/spell_editor_architecture.md`

---

## 7. Wichtigster nächster Arbeitsschritt

Der TargetNode-Vertrag ist definiert. Der nächste konkrete Schritt innerhalb von Issue #2 ist nun:

```text
Einen primitiven EffectNode vollständig gegentesten:
TransferThermalEnergy
am Beispiel
„Erhitze eine definierte Wassermenge um 10 K.“
```

Dabei zu klären:

1. Welche Zielrollen benötigt `TransferThermalEnergy`?
2. Ist `delta_temperature` oder `energy_amount` der primäre Parameter?
3. Wie werden Masse und Wärmekapazität aus dem TargetSet ermittelt?
4. Woher kommt die Energie?
5. Wie werden Kopplungsverluste und Abwärme behandelt?
6. Wird die Gesamtenergie vorab reserviert oder kontinuierlich übertragen?
7. Was geschieht bei unzureichender Energie: Abbruch, Teilwirkung oder proportionale Wirkung?
8. Wie wird der resultierende `StateChangeRequest` strukturiert?
9. Welche visuelle Glyphe und welche Code-Syntax repräsentieren diesen Knoten?

Danach können mechanische und kompositionelle EffectNodes dagegen getestet werden.

---

## 8. Offener Arbeitsmodus

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
