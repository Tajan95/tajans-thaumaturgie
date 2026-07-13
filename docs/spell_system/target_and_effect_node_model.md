# Target and Effect Node Model

**Stand:** 2026-07-14, 01:44 Europe/Berlin  
**Status:** Teilentscheidung / Arbeitsmodell für Issue #2

Dieses Dokument definiert den vorläufigen universellen Vertrag für Zielauswahl und atomare Wirkungen innerhalb eines Zaubers.

Es ergänzt:

- `spell_syntax.md`
- `spell_lifecycle_and_activation.md`
- `visual_spell_language.md`
- `../world_model/world_resolution_and_quantity_model.md`

---

## 1. Ebenentrennung

Für die weitere Arbeit werden drei Ebenen strikt getrennt:

```text
Theorie:
Welche physikalischen Zustände und Zustandsänderungen existieren?

Simulation:
Mit welcher räumlichen, zeitlichen und numerischen Auflösung werden sie berechnet?

Zaubersyntax:
Wie adressiert und beschreibt ein Zauber diese Zustandsänderungen?
```

Eine `WorldCell`, ein `TargetNode` und ein `EffectNode` sind daher nicht dieselbe Art von Einheit.

---

## 2. Grundmodell

```text
ActivationNode
    ↓
TargetNode(s)
    ↓
EffectNode(s)
    ↓
StateChangeRequest(s)
    ↓
Regel-, Kosten- und Erhaltungsprüfung
    ↓
SimulationCore
```

Dabei gilt:

```text
TargetNode → erzeugt eine explizite Zielmenge
EffectNode → fordert eine atomare Zustandsoperation auf dieser Zielmenge an
SimulationCore → prüft und verrechnet die resultierenden Zustandsänderungen
```

---

## 3. Universeller TargetNode-Vertrag

Ein `TargetNode` beschreibt nicht die Wirkung, sondern ausschließlich, **welche Weltanteile in welcher Rolle gebunden werden**.

Vorläufige Struktur:

```text
TargetNode {
    id
    selector
    anchor
    scope
    filters[]
    granularity
    binding_mode
    update_policy
    ordering
    limit
    access_constraints[]
    failure_policy
    output: TargetSet
}
```

### 3.1 Felder

| Feld | Bedeutung | Beispiele |
|---|---|---|
| `selector` | Grundart der Auswahl | Referenz, Position, Material, Relation, Query |
| `anchor` | Bezugspunkt oder Koordinatensystem | Zauberträger, Zauberer, Weltkoordinate, Zielobjekt |
| `scope` | räumlicher oder logischer Suchraum | Punkt, Kreis, Rechteck, Linie, Objekt, Chunk, Behälter |
| `filters` | zusätzliche Bedingungen | Material = Wasser, Phase = flüssig, Temperatur > 300 K |
| `granularity` | adressierte Auflösungsebene | Objekt, Zellmenge, Oberfläche, Stofffraktion |
| `binding_mode` | Zeitpunkt und Dauer der Bindung | `snapshot`, `live` |
| `update_policy` | Aktualisierungsrate bei Live-Bindung | pro Tick, alle n Ticks, ereignisbasiert |
| `ordering` | Sortierung einer Zielmenge | nächstes, wärmstes, schwerstes, zufällig |
| `limit` | maximale Zielanzahl oder Zielmasse | 1 Objekt, 20 Zellen, 10 g Stoff |
| `access_constraints` | Zugriffsvoraussetzungen | Sichtlinie, Kontakt, Reichweite, Bibliothekswissen |
| `failure_policy` | Verhalten bei leerer/ungültiger Zielmenge | abbrechen, überspringen, warten, neu suchen |

---

## 4. Selector-Familien

Vorläufig notwendige Selektorklassen:

| Selektor | Bedeutung | Beispiel |
|---|---|---|
| `ReferenceSelector` | bereits bekannte direkte Referenz | dieses Objekt, gebundener Kristall |
| `SpatialSelector` | Auswahl über Position und Form | alle Zellen in einem Kreis |
| `MaterialSelector` | Auswahl über Stoff-/Materialeigenschaften | Wasser, Eisen, gasförmiges CO₂ |
| `RelationalSelector` | Auswahl relativ zu einer Referenz | nächstes Objekt, Inhalt dieses Behälters |
| `PropertySelector` | Auswahl über Zustandswerte | Temperatur > 350 K |
| `QuerySelector` | informationsbasierte Suche | nächstes erkanntes Lebewesen |
| `CompositeSelector` | Kombination mehrerer Selektoren | Wasser innerhalb des markierten Gefäßes |

`QuerySelector` benötigt Informationsverarbeitung und ist deshalb in der Regel teurer als eine direkte Referenz oder eine rein räumliche Auswahl.

---

## 5. TargetSet und TargetRef

Ein TargetNode gibt ein `TargetSet` aus.

```text
TargetSet {
    members: TargetRef[]
    sampled_at_tick
    coordinate_frame
    granularity
    total_mass
    occupied_area
    effective_volume
}
```

Ein `TargetRef` ist eine typisierte Referenz:

```text
TargetRef :=
    ObjectRef
  | CellRef
  | CellRegionRef
  | SurfaceRef
  | MaterialFractionRef
  | PointRef
  | BiologicalRegionRef
```

### MaterialFractionRef

Für Spurengase, Legierungen, Lösungen oder heterogene Gemische muss ein Zauber Stoffanteile innerhalb von Zellen adressieren können:

```text
MaterialFractionRef {
    cell_or_region_ref
    component_id
    available_mass
    available_fraction
}
```

Dadurch kann ein Zauber beispielsweise CO₂ aus Luft auswählen, ohne dass das CO₂ vorher ein eigenes sichtbares Pixelvolumen besitzen muss.

---

## 6. Granularität und adaptive Auflösung

Der TargetNode soll angeben können, auf welcher Ebene ein Ziel gebunden wird:

```text
object
cell_set
surface
material_fraction
point_or_region
adaptive
```

`adaptive` bedeutet:

```text
solange möglich → aggregiertes Objekt verwenden
bei lokaler oder stofflicher Manipulation → feinere Zell-/Fraktionsauflösung anfordern
```

Beispiel:

```text
Bewege die Truhe
→ ObjectRef genügt

Trenne die Stahlbeschläge vom Holz
→ Material-/Objektkomponenten müssen detaillierter adressiert werden
```

---

## 7. Bindungsmodi

### Snapshot

```text
binding_mode: snapshot
```

Die Zielmenge wird zu einem definierten Zeitpunkt bestimmt und bleibt für die Ausführung gebunden.

Beispiel:

```text
Erhitze das Objekt, auf das beim Start gezeigt wurde.
```

### Live

```text
binding_mode: live
```

Die Zielmenge wird während der Laufzeit erneut ausgewertet.

Beispiel:

```text
Erhitze fortlaufend das nächste Metallobjekt.
```

Live-Bindung ist teurer, weil Suchraum, Filter und Bindung regelmäßig neu berechnet und thaumisch aufrechterhalten werden müssen.

Kostenfaktoren:

- Suchraumgröße
- Zahl und Komplexität der Filter
- Aktualisierungsrate
- Zielbewegung
- Zielanzahl
- Analyseauflösung
- notwendige Bibliotheksdefinitionen

---

## 8. Zielrollen

Ein EffectNode kann mehrere semantisch verschiedene Zielports besitzen.

Vorläufige Rollen:

```text
subject
source
recipient
source_location
 destination
reference_frame
energy_source
energy_sink
byproduct_sink
```

Beispiele:

### Bewegung

```text
subject: Stein
reference_frame: Welt oder Zauberer
```

### Wärmetransfer

```text
source: zu kühlendes Wasser
recipient / energy_sink: Umgebung oder Speicher
```

### Stofftrennung

```text
source: Luftgemisch
subject: CO₂-Fraktion
 destination: Sammelgefäß
```

Zielrollen werden als benannte Eingangsports des EffectNodes modelliert. Ein TargetNode selbst muss nicht wissen, wofür sein Output verwendet wird.

---

## 9. Universeller EffectNode-Vertrag

Ein primitiver `EffectNode` enthält genau **eine atomare Zustandsoperation**.

```text
EffectNode {
    id
    domain
    operation
    target_inputs: Map<TargetRole, TargetSet>
    parameters
    application_mode
    timing
    precision_requirement
    resource_binding
    output: StateChangeRequest[]
}
```

### Ein Effekt pro primitivem Knoten

```text
ApplyForce
TransferThermalEnergy
ApplyTorque
TransferCharge
TransportComponentMass
ChangeBondStructure
RequestPhaseTransition
ChangeNuclearComposition
```

Nicht als einzelnes Primitive:

```text
Erhitze + bewege + rotiere + lade
```

Mehrere Wirkungen werden durch parallele oder sequenzielle Graphzweige kombiniert.

---

## 10. Atomar bedeutet nicht zwingend nur ein Zustandsdelta

Eine atomare Operation darf mehrere gekoppelte Zustandsänderungen erzeugen, wenn diese untrennbar zur selben physikalischen Operation gehören.

Beispiel:

```text
TransferThermalEnergy
```

verringert die innere Energie der Quelle und erhöht die innere Energie der Senke. Trotzdem handelt es sich um eine atomare Transferoperation.

Dasselbe gilt für:

- Impulsübertragung mit Gegenimpuls
- Ladungstransfer
- Massentransport zwischen Herkunft und Ziel
- chemische Reaktionen mit Edukten, Produkten und Nebenprodukten

---

## 11. Effect-Domänen

Vorläufige Standarddomänen:

| Domäne | Veränderte Zustände | Beispielprimitive |
|---|---|---|
| mechanisch-kinematisch | Position, Geschwindigkeit, Impuls, Rotation | `ApplyForce`, `ApplyImpulse`, `ApplyTorque` |
| mechanisch-strukturell | Spannung, Dehnung, Form, Bruchzustand | `ApplyStress`, `Deform`, `Fracture` |
| thermisch | innere Energie, Temperatur, Wärmetransport | `TransferThermalEnergy` |
| elektrisch in Materie | Ladung, Ladungsverteilung, Stromfluss | `TransferCharge`, `DriveCurrent` |
| kompositionell / transportbezogen | Stoffverteilung und Komponentenmasse | `TransportComponentMass`, `ConcentrateComponent` |
| chemisch | Molekül- und Bindungsstruktur | `ChangeBondStructure`, `ExecuteReaction` |
| phasenbezogen | Aggregatzustand | `RequestPhaseTransition` |
| nuklear | Kern-/Isotopenzusammensetzung | `ChangeNuclearComposition` |

### Spätere High-Level-Domäne

Direkte substratlose Feld-, Wellen- oder Photonenmanipulation bleibt eine spätere High-Level-Interventionsklasse und gehört nicht zu den Standardprimitiven.

---

## 12. Informations-, biologische und kognitive Operationen

### Information ist keine normale Effect-Domäne

Suchen, Erkennen, Klassifizieren, Sortieren und Filtern verändern nicht zwangsläufig die materielle Welt.

Sie werden daher vorläufig als eigene Node-Familien behandelt:

```text
QueryNode
AnalysisNode
PredicateNode
ComparatorNode
```

Sie können TargetSets oder Informationswerte erzeugen, die anschließend von EffectNodes verwendet werden.

### Keine grundlegende Kognitions-Magie als Standardprimitive

`Gedanken lesen`, `Tierkommunikation` oder `Willen kontrollieren` werden vorläufig nicht als elementare EffectNodes eingeführt.

Stattdessen müssen solche Makros aus zugrunde liegenden Operationen ableitbar sein, beispielsweise:

```text
Tierkommunikation
= sensorische Signale analysieren
+ Muster klassifizieren
+ Bedeutung über Bibliothek abbilden
+ kompatible akustische/visuelle/chemische Signale erzeugen
```

```text
Beeinflussung eines Gehirns
= biologische Zielregion präzise auswählen
+ elektrische und/oder chemische Zustände verändern
+ kontinuierliches Feedback und Sicherheitslogik
```

Direkte mentale Fernwirkung ohne materielles neuronales Substrat ist keine Standardmagie.

Biologische und kognitive Makros sind möglich, aber durch Informationsmangel, hohe Komplexität, individuelle Gehirnstruktur, geringe Fehlertoleranz und erhebliche ethische sowie physische Risiken begrenzt.

---

## 13. Makros und Kompaktheit

Kompakte Zauber werden nicht durch Multi-Effect-Primitivknoten erzeugt, sondern durch Makros:

```text
MacroNode
→ expandiert zu internem Teilgraphen
```

Beispiel:

```text
Flammenprojektil
    ├─ materielles Medium auswählen
    ├─ thermische Energie übertragen
    ├─ ggf. ionisieren
    ├─ beschleunigen
    ├─ Flugbahn stabilisieren
    └─ beim Aufprall Energie und Impuls übertragen
```

Für Validierung, Kosten und Simulation wird immer der expandierte Graph verwendet.

---

## 14. Parallelität und Tick-Semantik

Mehrere EffectNodes dürfen parallel ausgeführt werden.

```text
              ┌→ ApplyForce
Activation ───┤
              └→ TransferThermalEnergy
```

Vorläufige Commit-Semantik:

```text
1. Tick-Ausgangszustand lesen
2. parallele StateChangeRequests berechnen
3. Konflikte, Ressourcen und Erhaltung prüfen
4. gültige Änderungen gemeinsam committen
5. Nebenprodukte und Fehlerzustände erzeugen
```

Dadurch hängt das Ergebnis paralleler Operationen nicht unbeabsichtigt von der internen Iterationsreihenfolge ab.

Konfliktregeln für widersprüchliche StateChangeRequests bleiben noch zu konkretisieren.

---

## 15. StateChangeRequest

Ein EffectNode verändert die Welt nicht direkt. Er erzeugt zunächst einen oder mehrere prüfbare Änderungsanträge.

```text
StateChangeRequest {
    operation_id
    target_refs[]
    state_deltas[]
    requested_rate_or_duration
    physical_minimum_work_J
    control_work_J
    source_requirements[]
    sink_requirements[]
    byproducts[]
    conservation_constraints[]
    precision_requirement
    failure_policy
}
```

Die Regelengine kann einen Antrag:

- vollständig zulassen,
- auf verfügbare Ressourcen begrenzen,
- verschieben,
- abbrechen,
- oder als Fehler zurückweisen.

---

## 16. Dynamische Effektkosten

Die Kosten eines EffectNodes werden nicht pauschal bei der Erstellung festgelegt, sondern aus Operation, Zielzustand und Parametern berechnet.

Beispiel:

```text
EffectNode:
    Temperaturänderung +10 K anfordern

Physik:
    benötigte Wärmeenergie = Masse × spezifische Wärmekapazität × 10 K
```

Der Node definiert die gewünschte Zustandsänderung. Materialdaten und aktueller Weltzustand bestimmen die physikalische Mindestarbeit.

---

## 17. Steuerarbeit des Zauberprogramms

Zusätzlich zur physikalischen Effektarbeit verbraucht die Ausführung der Zauberlogik thaumische Steuerarbeit.

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

Jede ausgeführte primitive Operation darf einen Basiskostenanteil besitzen. Dieser ist jedoch nicht als identische Pauschale pro sichtbarem Editor-Knoten zu verstehen.

```text
Steuerkosten =
    Grundaktivierung
  + primitive Operationen
  + Zielmengenkomplexität
  + Präzisionsanforderung
  + Verzweigungen und Parallelität
  + Aktualisierungsfrequenz
  + Feedbackschleifen
  + Sicherheitsprüfungen
```

Makros werden für die Kostenberechnung expandiert. Das Zusammenfassen mehrerer Operationen in einem sichtbaren Makro senkt daher nicht künstlich die Kosten.

---

## 18. Minimale Editor-Verbindungen

Der Editor sollte typisierte Ports verwenden.

```text
TargetNode.output: TargetSet
EffectNode.subject_input: TargetSet
EffectNode.energy_source_input: TargetSet
EffectNode.energy_sink_input: TargetSet
EffectNode.output: StateChangeRequest
```

Ungültige Verbindung:

```text
Temperaturwert → Objektport
```

Gültige Verbindung:

```text
WasserTargetSet → TransferThermalEnergy.subject
```

Makros dürfen Ports verbergen oder zusammenfassen, müssen intern aber dieselben Typregeln erfüllen.

---

## 19. Beispiel: Wasser um 10 K erwärmen

```text
ActivationNode:
    on_complete_execute_once

TargetNode:
    selector: MaterialSelector(Wasser)
    scope: definierte Kreisfläche
    granularity: adaptive
    binding_mode: snapshot
    output: WasserTargetSet

EffectNode:
    domain: thermisch
    operation: TransferThermalEnergy
    subject: WasserTargetSet
    parameter: delta_temperature = +10 K

ResourceTargetNode:
    selector: gebundener Energiespeicher
    output: EnergySourceTargetSet
```

Der EffectNode erzeugt danach einen `StateChangeRequest`. Die Regelengine berechnet aus Wassermasse, Wärmekapazität, Ausgangstemperatur, Kopplung und Verlusten die notwendigen Joule.

Noch offen bleibt dabei insbesondere, wohin Verlustwärme geht und ob die Energie vollständig vorab reserviert oder während der Ausführung übertragen wird.

---

## 20. Aktueller Status

### Festgelegt

- TargetNodes erzeugen explizite, typisierte TargetSets.
- EffectNodes konsumieren TargetSets über benannte Zielrollen.
- Primitive EffectNodes enthalten genau eine atomare Zustandsoperation.
- Physikalisch gekoppelte Gegenänderungen dürfen Teil derselben atomaren Transferoperation sein.
- Mehrere Effekte werden über Graphzweige parallel oder sequenziell kombiniert.
- Makros werden für Prüfung und Kosten vollständig expandiert.
- Live-Zielbindung ist teurer als Snapshot-Bindung.
- Zauberlogik verursacht zusätzlich zur physikalischen Effektarbeit Steuerarbeit.
- Informationsverarbeitung wird als eigene Node-Familie modelliert.
- Kognitive oder biologische Zauber sind keine elementaren Standardprimitive.

### Starke Hypothese

```text
Interne Zauberform = Komponentenobjekt + typisierter gerichteter Wirkungsgraph
```

### Offene Fragen

- Welche TargetRef-Typen braucht der erste Prototyp tatsächlich?
- Welche Filter dürfen ohne Analysebibliothek verwendet werden?
- Wie werden widersprüchliche parallele StateChangeRequests aufgelöst?
- Darf ein EffectNode teilweise ausgeführt werden, wenn nur ein Teil der Energie verfügbar ist?
- Welche atomaren Effect-Operationen bilden die minimale Standardbibliothek?
- Wie hoch sind Basis- und Komplexitätskosten einzelner Node-Familien?
- Wie werden biologische Zielregionen formal und sicher adressiert?
