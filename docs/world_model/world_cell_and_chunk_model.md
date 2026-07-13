# 20 — World Cell and Chunk Model

**Stand:** 2026-07-14, 01:44 Europe/Berlin  
**Status:** Arbeitsmodell / Prototyping-Grundlage

Dieses Dokument beschreibt das datenorientierte Zell-/Chunk-Modell der 2D-Materialwelt.

Ergänzende Details:

- `world_resolution_and_quantity_model.md`
- `2d_world_simulation_model.md`
- `material_world_model.md`

---

## 1. Grundannahme

```text
Die Welt besteht aus vielen kleinen WorldCells,
die in WorldChunks gruppiert werden.
```

Eine WorldCell ist der kleinste räumlich adressierbare Ort der Materialwelt.

```text
WorldCell = räumliche Simulationseinheit
```

Sie ist ausdrücklich nicht:

- ein eigenständiges Engine-Objekt,
- eine Mindestmasse,
- eine Mindeststoffmenge,
- ein vollständiges physikalisches Teilchen,
- zwingend genau ein sichtbarer Bildschirmpixel.

---

## 2. Keine Engine-Entität pro Zelle

Nicht verwenden, solange kein Benchmark das Gegenteil beweist:

```text
1 Zelle = 1 Godot Node / Unity GameObject / Bevy Entity
```

Bevorzugt:

```text
viele Zellen als kompakte Datenarrays
→ SimulationCore verarbeitet Arrays/Chunks
→ Renderer erzeugt Textur oder Layer
```

---

## 3. 2D-Seitenansicht und Layer

Der erste Prototyp verwendet eine 2D-Seitenansicht.

```text
x = horizontal
y = vertikal
```

Optional existieren diskrete Tiefenebenen:

```text
0 = Hintergrund
1 = Hauptebene
2 = Vordergrund
```

Jede WorldCell wird daher durch mindestens folgende räumliche Adresse identifiziert:

```text
(layer_id, grid_x, grid_y)
```

---

## 4. WorldCell-Minimalmodell

Für einen ersten Zellbenchmark:

```text
WorldCell {
    dominant_material_id
    temperature
    bulk_velocity_x
    bulk_velocity_y
    occupied_fraction
    composition_ref
    flags
}
```

| Feld | Bedeutung |
|---|---|
| `dominant_material_id` | Darstellungs-/Schnellzugriff auf dominantes Material |
| `temperature` | lokaler thermischer Zustand |
| `bulk_velocity_x/y` | mittlerer Bewegungsvektor von Flussmaterial |
| `occupied_fraction` | belegter Anteil des effektiven Zellvolumens |
| `composition_ref` | Verweis auf tatsächliche Stoffmassen und Phasen |
| `flags` | aktiv, dirty, ruhend, brennend, geschützt usw. |

Die physikalische Zusammensetzung darf nicht allein aus `dominant_material_id` abgeleitet werden.

---

## 5. Erweiterte WorldCell-Daten

Später mögliche Felder:

| Feld | Bedeutung |
|---|---|
| `pressure` | lokaler Gas-/Flüssigkeitsdruck |
| `phase_summary` | dominanter oder aggregierter Phasenzustand |
| `charge` | elektrische Ladung / Ladungsverteilung |
| `field_value` | lokaler thaumischer oder Debugwert |
| `spell_effect_ref` | aktive StateChangeRequests oder Effekte |
| `last_updated_tick` | Aktivitäts-/Updateoptimierung |
| `object_occupancy_ref` | starres Objekt, das die Zelle rasterisiert belegt |
| `numerical_residual` | konservierter Rundungs-/Quantisierungsrest |

Diese Felder werden nur eingeführt, wenn ein konkreter Benchmark oder Effekt sie benötigt.

---

## 6. Composition-Struktur

Sub-Zell-Massen werden außerhalb der WorldCell in einer Composition-Struktur gespeichert.

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
    phase
}
```

Beispiel:

```text
Luftzelle:
- N₂: 0,92 g
- O₂: 0,25 g
- CO₂: 0,0005 g
- weitere Spuren
```

Die Werte sind Beispiele, keine festgelegte atmosphärische Zellmasse.

---

## 7. Sichtbares Hauptmaterial

Der Renderer darf eine vereinfachte Darstellung verwenden:

```text
dominant_material_id
```

Mögliche Auswahlregeln:

- größter Massenanteil,
- größter Volumenanteil,
- dominante Materialklasse,
- gameplayrelevanter Bestandteil,
- Analyse-Overlay statt Normaldarstellung.

Die Darstellungsregel verändert keine physikalische Masse oder Zusammensetzung.

---

## 8. Belegungslogik

Für kondensierte Stoffe:

```text
occupied_volume_i = mass_i / density_i
occupied_fraction_i = occupied_volume_i / cell_volume_effective
```

Grundsätzlich:

```text
Σ occupied_fraction_i ≤ 1
```

Ausnahmen oder andere Modelle sind für kompressible Gase, Porosität und explizite Mehrphasenmodelle möglich.

Makroskopische Festkörper dürfen nicht allein aufgrund kleiner Volumenanteile frei ineinander überlappen. Ihre Objekt- und Kollisionsgeometrie bleibt maßgeblich.

---

## 9. Komponentenanzahl und CompositionPool

Es gibt kein semantisches Limit dafür, wie viele Stoffe eine Zelle enthalten kann.

Eine unbegrenzte individuelle Liste pro Zelle wäre jedoch ineffizient.

Empfohlenes technisches Modell:

```text
kleiner Inline-Speicher für häufige einfache Fälle
+ composition_ref auf externen CompositionPool
```

Erste Benchmarkkandidaten:

```text
4 Inline-Komponenten
oder
8 Inline-Komponenten
```

Mögliche Optimierungen:

- gemeinsame unveränderliche Datensätze für häufige Gemische,
- Copy-on-Write bei Änderungen,
- Trace-Records für konservierte Spuranteile,
- explizite Auflösung einer Spur erst bei Analyse oder Manipulation.

---

## 10. WorldChunk

```text
WorldChunk = Verwaltungsblock für benachbarte WorldCells
```

Beispielgrößen:

```text
16 × 16
32 × 32
64 × 64
```

Vorläufige Struktur:

```text
WorldChunk {
    layer_id
    chunk_x
    chunk_y
    cells[]
    active
    dirty
    bounds
    total_mass
    total_energy
    total_momentum_x
    total_momentum_y
    active_cell_count
}
```

Chunks ermöglichen:

- nur aktive Regionen zu simulieren,
- lokale Kollisionen und Nachbarschaften,
- regionale Massen- und Energiebilanzen,
- gebündelte Renderupdates,
- Container-/Raumerkennung,
- LOD und Aggregation,
- Streaming großer Welten.

---

## 11. Datenfluss

```text
Input / SpellIR
    ↓
TargetNodes erzeugen TargetSets
    ↓
EffectNodes erzeugen StateChangeRequests
    ↓
SimulationCore validiert und verändert Weltzustand
    ↓
Chunks werden active / dirty
    ↓
RendererAdapter aktualisiert Material- und Analyse-Layer
    ↓
DebugOverlay zeigt Metriken und Bilanzen
```

```text
Die Engine zeichnet und nimmt Input an.
Der SimulationCore entscheidet, was physikalisch passiert.
```

---

## 12. Starre Objekte

Starre Objekte liegen nicht vollständig als unabhängige Zellpartikel vor.

```text
RigidObject {
    object_id
    layer_id
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

WorldCells speichern nur ihre rasterisierte Belegung oder einen Verweis auf das Objekt.

```text
kontinuierliche / Fixed-Point-Pose
→ rasterisierte Zellbelegung
```

Bei Bruch, Schmelzen oder lokaler stofflicher Manipulation kann ein Objekt in Fragmente, Zellen oder Flussmaterial überführt werden.

---

## 13. Flussmaterialien

Granulate, Flüssigkeiten und Gase verwenden zellbasierte Transfers.

### Sand / Granulate

```text
wenn unten frei → Masse verschieben
sonst diagonal / seitlich prüfen
sonst ruhen
```

### Flüssigkeit

```text
Masse + Impuls + Wärme
→ an geeignete Nachbarzellen übertragen
```

### Gas

```text
Stoffmenge + Druck + Wärme
→ diffundieren / strömen / expandieren
```

Transferoperationen müssen Komponentenmasse, Energie und Impuls bilanzieren.

---

## 14. Sub-Zell-Positionen und Rasterisierung

Starre Objekte verwenden Sub-Zell-Positionen:

```text
x = 27,318 Zellen
y = 14,752 Zellen
```

Die Darstellung und Kollisionsbelegung werden daraus rasterisiert.

Vorteile:

- saubere Parabelbahnen,
- langsame Bewegung unter einer Zelle pro Tick,
- weniger Grid-Richtungsartefakte,
- bessere Rotations- und Kollisionsmodelle.

Optional kann ein ruhendes Objekt kontrolliert in eine stabile Rasterbelegung einrasten.

Restenergie wird als Wärme oder numerisches Residuum verbucht.

---

## 15. Numerische Speicherung

Semantische physikalische Einheiten:

- Meter
- Gramm
- Sekunde
- Kelvin
- Joule
- Newton
- Watt

Starke Implementationshypothese:

```text
Fixed-Point-Integer statt unkontrollierter Float-Drift
```

Erster Energiebenchmark:

```text
1 interne Energieeinheit = 1 mJ
Datentyp = signed 64-bit integer
```

Die endgültigen Quanten für Masse, Energie und Position werden durch Benchmarks festgelegt.

---

## 16. Speicherlayout

### Array of Structs

```text
cells = [WorldCell, WorldCell, WorldCell, ...]
```

Vorteil:

- einfach zu verstehen und zu debuggen.

### Struct of Arrays

```text
material_ids[]
temperatures[]
velocity_x[]
velocity_y[]
occupied_fractions[]
composition_refs[]
flags[]
```

Vorteil:

- oft cache- und vektorisierungsfreundlicher.

### Empfehlung

```text
Dokumentation / erste Logik:
Array of Structs denken

Performance-Benchmark:
Struct of Arrays oder chunkbasierte Hybridform testen
```

---

## 17. Darstellungsschichten

Aus denselben Simulationsdaten können mehrere Overlays erzeugt werden:

| Layer | Datenquelle |
|---|---|
| Material-Layer | `dominant_material_id`, Composition |
| Temperatur-Layer | `temperature` |
| Vektor-Layer | Geschwindigkeit und Impuls |
| Analyse-Layer | Stoffmassen, Gemischtyp, Materialattribute |
| Zauber-Layer | TargetSets, StateChangeRequests, Reichweiten |
| UI/HUD | FPS, Tickzeit, Bilanzen, aktive Chunks |

---

## 18. Erhaltungs- und Debugwerte

Mindestens messbar:

- Gesamtmasse
- Gesamtenergie
- Gesamtimpuls
- Masse pro Komponente
- numerische Residuen
- aktive Zellen
- aktive Chunks
- dirty Chunks
- Simulationszeit pro Tick
- Renderzeit

Für Trennung oder chemische Reaktion muss die Komponentenbilanz prüfbar bleiben.

---

## 19. Minimaler erster Benchmark

WorldCell-Felder:

```text
dominant_material_id
temperature
bulk_velocity_x
bulk_velocity_y
occupied_fraction
composition_ref
flags
```

Materialien:

```text
0 = Luft
1 = Sand
2 = Wasser
3 = Stein
```

Erste Tests:

1. fallender Sand
2. lokale Erwärmung mit Temperatur-Overlay
3. Sub-Zell-Komponente in einer Luftzelle speichern
4. Masse zwischen zwei Zellen transferieren
5. Massen- und Energiebilanz anzeigen

---

## 20. Offene Fragen

1. Welche Zellbreite und Zellhöhe werden verwendet?
2. Welche effektive Tiefe besitzt eine diskrete Ebene?
3. Welche Chunkgröße ist sinnvoll?
4. Array of Structs, Struct of Arrays oder Hybrid?
5. Vier oder acht Inline-Komponenten?
6. Wie werden Trace-Records und Copy-on-Write umgesetzt?
7. Wie werden Flüssigkeits- und Gastransfers zwischen Chunks behandelt?
8. Wann wird ein RigidObject in Fragmente oder Zellen zerlegt?
9. Wie werden Kollisionsformen aus Sub-Zell-Positionen rasterisiert?
10. Welche Fixed-Point-Quanten verhindern Drift ohne unnötigen Rechenaufwand?
11. Sind Vorder- und Hintergrund voll physikalisch?
12. Wie werden Container und geschlossene Räume erkannt?
