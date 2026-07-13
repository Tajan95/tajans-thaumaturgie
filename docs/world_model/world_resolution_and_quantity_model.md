# World Resolution and Quantity Model

**Stand:** 2026-07-14, 01:44 Europe/Berlin  
**Status:** Teilentscheidung / Arbeitsmodell für Welt- und Physiksimulation

Dieses Dokument trennt räumliche, stoffliche, zeitliche und numerische Auflösung der 2D-Welt.

Es ergänzt:

- `material_world_model.md`
- `2d_world_simulation_model.md`
- `world_cell_and_chunk_model.md`
- `../spell_system/target_and_effect_node_model.md`

---

## 1. Zielbild des ersten Prototyps

Der erste spielbare Simulationsprototyp wird als **2D-Seitenansicht** gedacht.

```text
x = horizontale Weltachse
y = vertikale Weltachse
z = keine kontinuierlich simulierte Raumachse
```

Optional können drei diskrete Tiefenebenen verwendet werden:

```text
Hintergrund
Hauptebene
Vordergrund
```

Diese Ebenen sind keine vollständige 3D-Simulation. Sie sind getrennte 2D-Raster bzw. diskrete Tiefenspuren. Wechselwirkungen zwischen ihnen müssen explizit definiert werden.

---

## 2. Physikalische Bezugsgrößen

Die Theorie und die Zaubersyntax verwenden SI-kompatible physikalische Größen.

Vorläufig bevorzugte Arbeits- und Anzeigeeinheiten für den 2D-Prototyp:

| Größe | Einheit |
|---|---|
| Entfernung / Geometrie | Meter (`m`) |
| Masse | Gramm (`g`) |
| Zeit | Sekunde (`s`) |
| Temperatur | Kelvin (`K`) |
| Energie / Arbeit | Joule (`J`) |
| Leistung | Watt (`W`) |
| Kraft | Newton (`N`) |
| elektrische Ladung | Coulomb (`C`) |

Dabei gilt weiterhin:

```text
1 J = 1 N · m = 1 W · s
```

Die Wahl von Gramm als praktische Masseeinheit ändert die physikalischen Gleichungen nicht. Eine Einheiten- und Konvertierungsschicht muss sicherstellen, dass Formeln intern konsistent bleiben.

---

## 3. 2D-Fläche und effektives Volumen

Obwohl die Welt funktional zweidimensional simuliert wird, benötigen Dichte, Gasmenge und Wärmekapazität ein Volumenmodell.

Dafür erhält jede diskrete Tiefenebene eine angenommene effektive Tiefe:

```text
cell_area = cell_width × cell_height
cell_volume_effective = cell_area × layer_depth
```

`layer_depth` ist eine Simulationskonstante oder ein Levelparameter. Dadurch können reale Volumendichten genutzt werden, ohne eine kontinuierliche z-Achse zu simulieren.

Alternative 2D-Flächendichten bleiben für spätere Benchmarks möglich, werden aber nicht als Standardmodell bevorzugt, weil sie eine spätere 3D-Übertragung erschweren würden.

---

## 4. Getrennte Auflösungsdimensionen

Mindestens folgende Auflösungen werden unabhängig voneinander behandelt:

| Auflösung | Bedeutung |
|---|---|
| Raumauflösung | Breite und Höhe einer WorldCell |
| Tiefenauflösung | diskrete Ebene und deren angenommene Tiefe |
| Massenauflösung | kleinste numerisch speicherbare Massendifferenz |
| Zusammensetzungsauflösung | kleinster speicherbarer Stoffanteil |
| Zeitauflösung | Dauer eines Simulationsticks |
| Energieauflösung | kleinste numerisch unterscheidbare Energiemenge |
| Positionsauflösung | Sub-Zell-Präzision bewegter Objekte |

Wichtig:

```text
WorldCell-Größe ≠ Mindestmasse ≠ Mindestenergie ≠ Mindeststoffanteil
```

---

## 5. Energiepräzision und Integer-Arithmetik

Ein Joule ist die semantische Einheit der Energie, aber nicht zwingend das kleinste berechenbare Energiequantum.

`1 J` als Mindestauflösung wäre für kleine Massen, Spurstoffe und langsame Prozesse zu grob.

Vorläufige Implementationsrichtung:

```text
semantische Einheit: Joule
interne Speicherung: Fixed-Point-Integer in kleineren Energiequanten
```

Erster Benchmarkkandidat:

```text
1 interne Energieeinheit = 1 Millijoule = 0,001 J
Datentyp = signed 64-bit integer
```

Vorteile:

- deterministischere Berechnung als mit frei driftenden Gleitkommazahlen
- klar quantisierte Energie- und Kostenbilanzen
- kleine Prozesse bleiben darstellbar
- große Energiebereiche passen weiterhin in 64 Bit
- reproduzierbare Tests werden erleichtert

Die endgültige Quantisierung (`J`, `mJ`, `µJ` oder anderes) wird erst nach Benchmark und Größenabschätzung festgelegt.

Dasselbe Prinzip kann für Masse, Position und Stoffmengen verwendet werden:

```text
mass_internal = integer mass quanta
energy_internal = integer energy quanta
position_internal = fixed-point sub-cell coordinates
```

---

## 6. WorldCell als räumliche Einheit

Eine `WorldCell` ist die kleinste räumlich adressierbare Simulationseinheit, nicht die kleinste Materiemenge.

Vorläufiges Modell:

```text
WorldCell {
    layer_id
    grid_x
    grid_y
    occupied_fraction
    dominant_material_id
    phase_summary
    temperature
    bulk_velocity
    composition_ref
    flags
}
```

Eine Zelle kann:

- vollständig gefüllt sein,
- teilweise gefüllt sein,
- ein Gasgemisch enthalten,
- mehrere Sub-Zell-Stoffmassen enthalten,
- visuell als ein dominantes Material erscheinen,
- intern eine komplexere Zusammensetzung bewahren.

---

## 7. Zusammensetzung und Sub-Zell-Massen

```text
Composition {
    components[]
    total_mass
    occupied_volume
    mixture_type
}
```

```text
ComponentAmount {
    component_id
    mass
    optional_phase
}
```

Beispiel einer Luftzelle:

```text
N₂: 0,92 g
O₂: 0,25 g
CO₂: 0,0005 g
weitere Spuren
```

Das CO₂ benötigt kein eigenes sichtbares Pixel. Ein Trennzauber kann den CO₂-Anteil direkt als `MaterialFractionRef` adressieren und aus mehreren Zellen akkumulieren.

---

## 8. Sichtbarkeit ist nicht gleich Existenz

Ein Stoff kann physikalisch gespeichert sein, ohne als eigenständige Zelle sichtbar zu werden.

```text
physikalische Mindestmenge
≠ sichtbare Mindestmenge
```

Der Renderer kann das dominante Material oder eine Materialklasse anzeigen.

Mögliche Darstellungsregel:

```text
wenn ein Bestandteil den größten sichtbaren Anteil stellt
→ Zelle erhält dessen Materialdarstellung
```

Für eine vorher leere bzw. vakuumartige Zelle kann bereits die kleinste simulierte Masse eines neu eintretenden Stoffes sichtbar gemacht werden, sofern dies für Gameplay oder Analyse sinnvoll ist.

Darstellungsgrenzen dürfen die physikalische Massenbilanz nicht verändern.

---

## 9. Zellbelegung durch Dichte

Für einen Stoffanteil gilt näherungsweise:

```text
occupied_volume_i = mass_i / density_i
occupied_fraction_i = occupied_volume_i / cell_volume_effective
```

Für kondensierte Materie muss grundsätzlich gelten:

```text
Σ occupied_fraction_i ≤ 1
```

Gasgemische können über Druck, Temperatur und Stoffmenge modelliert werden; ihre Belegung folgt nicht derselben starren Packungslogik wie inkompressible Feststoffe oder Flüssigkeiten.

---

## 10. Geteilte Zellen und Gemischtypen

Mehrere Stoffe dürfen dieselbe Zelle teilen, wenn ihre physikalische Situation dies erlaubt.

| Gemischtyp | Beispiel | Modell |
|---|---|---|
| homogen | Luft, Salzwasser, Legierung | gemeinsame Zusammensetzung |
| heterogene Partikel | Goldstaub in Sand | mehrere Komponenten im Partikelgemisch |
| porös / teilgefüllt | Schaum, lockerer Boden | Feststoff + Gas-/Flüssigkeitsanteil |
| getrennte Sub-Zell-Geometrie | zwei kleine Fragmente | gemeinsame Zelle, aber getrennte lokale Belegung |
| makroskopische Festkörper | zwei Kisten | getrennte Objektgeometrien, kein freies Überlappen |

Zwei größere Festkörper dürfen nicht allein deshalb dieselbe Zelle belegen, weil ihre aufsummierten Volumenanteile kleiner als eins wären. Ihre Objektgeometrie und Kollisionsbelegung bleiben relevant.

---

## 11. Anzahl der Komponenten pro Zelle

Eine unbegrenzte individuelle Komponentenliste pro WorldCell wäre speicher- und performanceintensiv.

Empfohlene technische Lösung:

```text
kein semantisches Stofflimit
+ kleiner schneller Inline-Speicher
+ externer CompositionPool für komplexe Fälle
```

Beispiel:

```text
Inline-Komponenten: 4 oder 8
Overflow: composition_ref → CompositionPool
```

Zusätzliche Optimierungen:

- häufige Mischungen wie Luft teilen sich unveränderliche Composition-Definitionen
- Änderungen verwenden Copy-on-Write
- sehr kleine Spuranteile können in einem konservierten Trace-Record zusammengefasst werden
- bei Analyse oder Manipulation werden benötigte Spuren wieder explizit aufgelöst

Dadurch existiert kein hartes magietheoretisches Limit, während typische Zellen kompakt bleiben.

Die genaue Inline-Kapazität wird im Benchmark festgelegt.

---

## 12. Akkumulation und Trennung von Spurstoffen

Beispiel: CO₂ aus Raumluft sammeln.

```text
1. TargetNode wählt Luftzellen.
2. MaterialFractionRef bindet den CO₂-Anteil jeder Zelle.
3. TransportComponentMass entfernt quantisierte CO₂-Masse aus den Quellen.
4. Dieselbe Masse wird in Zielzelle oder Behälter akkumuliert.
5. Renderer aktualisiert die sichtbare Darstellung, sobald Schwellen erreicht werden.
```

Masse darf bei diesem Prozess weder auf volle Zellen aufgerundet noch verworfen werden.

---

## 13. Hierarchische Objektauflösung

Makroskopische stabile Festkörper werden möglichst als aggregierte Objekte simuliert.

```text
RigidObject {
    geometry
    position_subcell
    orientation
    mass
    center_of_mass
    linear_velocity
    angular_velocity
    material_composition
    collision_shape
}
```

```text
stabiler Gegenstand
→ aggregierte Objektphysik

lokale stoffliche Manipulation
→ detailliertere Zell-/Komponentenauflösung

Bruch, Schmelzen oder Zerfall
→ Fragmente, Zellen oder Flussmaterial
```

Die Simulation erhöht ihre Detailtiefe nur, wenn die konkrete Interaktion dies erfordert.

---

## 14. Bewegungsmodell

### Starre Objekte

Starre Objekte verwenden:

```text
kontinuierliche oder Fixed-Point-Sub-Zell-Position
+ kontinuierliche Geschwindigkeits- und Rotationswerte
+ rasterisierte Belegung für Darstellung und lokale Interaktion
```

Dadurch sind langsame Bewegungen, Parabelbahnen und nicht achsenparallele Bewegungen möglich, ohne das Weltgrid aufzugeben.

### Granulate, Flüssigkeiten und Gase

Diese Materialklassen verwenden bevorzugt:

```text
zellbasierten Massen-, Impuls- und Energietransfer
```

Beispiele:

- Sand fällt oder rutscht zwischen Zellen.
- Flüssigkeit überträgt Masse und Impuls an Nachbarzellen.
- Gase verteilen Stoffmenge, Druck und Wärme über Zellgrenzen.

---

## 15. Ruhende Objekte und Grid-Snapping

Für ruhende oder sehr langsame Objekte kann später ein optionales Einrasten in das Zellraster geprüft werden.

```text
wenn Geschwindigkeit und Restbewegung unter Schwellwert
→ Objekt kann in stabile Rasterbelegung überführt werden
```

Ein solches Snapping darf numerische Energiefehler nicht stillschweigend verstecken.

Restenergie oder Differenzen werden bevorzugt:

- als Reibungswärme verbucht,
- in einem lokalen numerischen Residualkonto erfasst,
- oder durch einen expliziten Bilanzkorrekturschritt ausgeglichen.

Globale Sonnen-, Erd- oder Abstrahlungsflüsse existieren unabhängig davon, sollen aber keine unkontrollierten Simulationsfehler kaschieren.

---

## 16. Dreischichtige 2D-Welt

Vorläufige Architekturhypothese:

```text
Layer 0: Hintergrund
Layer 1: Hauptebene
Layer 2: Vordergrund
```

Jeder Layer besitzt ein eigenes 2D-Zellraster und eigene Objektbelegung.

Mögliche explizite Cross-Layer-Operationen:

- Objekt wechselt Tiefenebene
- Zauber adressiert mehrere Ebenen
- Wärme/Strahlung wird zwischen Ebenen gekoppelt
- Vordergrund verdeckt, aber blockiert nicht zwingend
- physische Verbindung über Portale, Öffnungen oder definierte Übergänge

Ob alle drei Ebenen physikalisch vollwertig oder teilweise nur visuell sind, bleibt eine Prototypentscheidung.

---

## 17. Verbindung zur Zaubersyntax

TargetNodes müssen die unterschiedlichen Auflösungsebenen adressieren können:

```text
ObjectRef
CellRef
CellRegionRef
MaterialFractionRef
SurfaceRef
LayerRef
```

EffectNodes arbeiten nicht direkt auf sichtbaren Pixeln, sondern auf den gebundenen physikalischen Referenzen.

Beispiel:

```text
Bewege den Stein
→ ObjectRef + ApplyForce

Erhitze die linke Hälfte des Steins
→ CellRegionRef/SurfaceRef + TransferThermalEnergy

Trenne Goldspuren aus dem Stein
→ MaterialFractionRef + TransportComponentMass
```

---

## 18. Aktueller Status

### Festgelegt

- Der erste Prototyp wird als 2D-Seitenansicht gedacht.
- Eine WorldCell ist eine räumliche Einheit, keine Mindestmasse oder Mindeststoffmenge.
- Sub-Zell-Massen und Stofffraktionen bleiben physikalisch erhalten.
- Sichtbare Darstellung und physikalische Zusammensetzung sind getrennt.
- Starre Objekte verwenden Sub-Zell-Positionen; Flussmaterialien nutzen Zelltransfermodelle.
- Simulationsauflösung wird lokal und bedarfsabhängig erhöht.
- Physikalische Größen werden SI-kompatibel geführt; Joule bleibt Energie-/Arbeitseinheit.

### Starke Hypothesen

- Drei diskrete Tiefenebenen sind für die 2D-Seitenansicht ausreichend.
- Fixed-Point-Integer sind für Masse, Energie und Position geeigneter als uneingeschränkte Gleitkommaarithmetik.
- Millijoule sind ein sinnvoller erster Energiequantisierungs-Benchmark.
- Zellen verwenden kleinen Inline-Komponentenspeicher plus externen CompositionPool.
- Ruhende starre Objekte können später kontrolliert ins Raster einrasten.

### Offene Fragen

- Welche Zellbreite und Zellhöhe werden verwendet?
- Welche effektive Tiefe besitzt eine Ebene?
- Welche Massen-, Energie- und Positionsquanten sind im Benchmark sinnvoll?
- Wie viele Inline-Komponenten besitzt eine Zelle: 4, 8 oder anderer Wert?
- Wie werden Druck und Stoffmenge von Gasen konkret berechnet?
- Wann wird ein aggregiertes Objekt in Zellen oder Fragmente zerlegt?
- Sind Hintergrund und Vordergrund voll physikalisch oder teilweise nur visuell?
- Welche Cross-Layer-Wechselwirkungen sind erlaubt?
