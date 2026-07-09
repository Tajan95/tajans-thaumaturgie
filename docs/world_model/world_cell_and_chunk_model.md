# 20 — World Cell and Chunk Model

Dieses Dokument beschreibt ein frühes Datenmodell für die 2D-Materialwelt.

**Status:** Arbeitsmodell / Prototyping-Grundlage

---

## Zweck

Bevor eine Engine endgültig gewählt wird, muss klar sein, welche Daten die Welt überhaupt speichern und verändern muss.

Die Engine-Frage hängt direkt davon ab, ob die Welt aus wenigen Objekten, vielen Partikeln, Pixeln, Zellen oder Chunks besteht.

Für Tajan's Thaumaturgie ist die vorläufige Annahme:

```text
Die Welt besteht aus vielen kleinen Weltzellen,
die in größere Chunks gruppiert werden.
```

---

## Begriff: WorldCell

Eine `WorldCell` ist die kleinste räumliche Simulationseinheit der 2D-Welt.

Sie ist nicht zwingend ein sichtbarer Pixel auf dem Bildschirm, aber sie kann als Pixel oder kleiner Block dargestellt werden.

Eine WorldCell enthält nicht „ein Objekt“, sondern einen lokalen Ausschnitt des Weltzustands.

```text
WorldCell = kleinster berechneter Ort der Materialwelt
```

## Warum keine Engine-Objekte pro Zelle?

Eine naive Umsetzung wäre:

```text
1 Zelle = 1 Godot Node / Unity GameObject / Bevy Entity
```

Das wäre für große Mengen vermutlich zu langsam und zu schwer zu verwalten.

Stattdessen sollen Zellen als kompakte Daten in Arrays oder Chunks gespeichert werden.

```text
viele Zellen als Datenarray → ein Renderer zeichnet daraus ein Bild
```

---

## Minimale WorldCell-Daten

Für einen ersten Prototyp sollte eine Zelle nur wenige Pflichtfelder besitzen.

| Feld | Bedeutung | Beispiel |
|---|---|---|
| `material_id` | Hauptmaterial der Zelle | Luft, Sand, Wasser, Stein |
| `phase` | Aggregatzustand | fest, flüssig, gasförmig, Plasma |
| `temperature` | Temperaturwert | 293 K |
| `velocity` | Bewegungsvektor | x/y-Richtung + Geschwindigkeit |
| `mass` | lokale Masse oder Materialmenge | 1.0 Zellmasse |
| `flags` | Zustandsbits | aktiv, ruhend, brennend, geschützt |

Vorläufiges Minimalmodell:

```text
WorldCell {
    material_id
    phase
    temperature
    velocity_x
    velocity_y
    mass
    flags
}
```

## Erweiterte WorldCell-Daten

Später können weitere Felder hinzukommen:

| Feld | Bedeutung |
|---|---|
| `pressure` | Druck / Gas- oder Flüssigkeitsdruck |
| `charge` | elektrische Ladung oder Ladungsverteilung |
| `field_value` | lokaler Feld- oder Debugwert |
| `composition_ref` | Verweis auf Materialfraktionen |
| `spell_effect_ref` | aktiver Zaubereffekt an dieser Zelle |
| `last_updated_tick` | Optimierung für aktive Bereiche |
| `chunk_id` | Zugehörigkeit zu einem Chunk |

Diese Felder sollten nicht sofort alle implementiert werden. Zu viele Felder machen frühe Tests schwerer.

---

## Begriff: Materialfraktion

Eine Zelle kann ein sichtbares Hauptmaterial besitzen, aber intern aus mehreren Fraktionen bestehen.

Beispiel:

```text
Luft = 78% Stickstoff + 21% Sauerstoff + Restfraktionen
```

oder:

```text
Gestein = Silikate + Eisenanteile + Spuren von Gold/Platin
```

Für den ersten Prototyp kann die Fraktion optional sein.

Mögliches Modell:

```text
composition_ref → zeigt auf eine externe Composition-Struktur
```

Dadurch muss nicht jede einzelne Zelle eine lange Liste aller Bestandteile speichern.

---

## Begriff: WorldChunk

Ein `WorldChunk` ist eine Gruppe benachbarter WorldCells.

Beispiel:

```text
1 Chunk = 32 × 32 Zellen
oder
1 Chunk = 64 × 64 Zellen
```

Chunks helfen, die Welt nicht immer komplett berechnen zu müssen.

```text
WorldChunk = Verwaltungsblock für viele WorldCells
```

## Warum Chunks sinnvoll sind

Chunks ermöglichen:

- nur aktive Regionen zu berechnen
- Kollisionen lokal zu prüfen
- Wärme/Gase regional zu aggregieren
- Speicher besser zu organisieren
- Debugwerte pro Region zu berechnen
- große Welten streambar zu machen
- Renderdaten gebündelt zu aktualisieren

Ohne Chunks müsste jeder Tick potenziell die ganze Welt prüfen.

Mit Chunks kann das System sagen:

```text
Nur diese Region hat sich verändert → nur diese Chunks aktualisieren.
```

---

## Minimale WorldChunk-Daten

| Feld | Bedeutung |
|---|---|
| `chunk_x`, `chunk_y` | Position im Chunkraster |
| `cells` | Datenarray der enthaltenen Zellen |
| `active` | ob der Chunk aktuell simuliert werden muss |
| `dirty` | ob Darstellung/Debug neu gezeichnet werden muss |
| `total_mass` | Massenbilanz des Chunks |
| `total_energy` | grobe Energiebilanz des Chunks |
| `bounds` | räumlicher Bereich |

Beispielstruktur:

```text
WorldChunk {
    chunk_x
    chunk_y
    cells[]
    active
    dirty
    total_mass
    total_energy
}
```

---

## Datenfluss

Das Grundmodell sollte ungefähr so funktionieren:

```text
Input / Zauber
    ↓
SimulationCore verändert WorldCells
    ↓
Chunks markieren sich als dirty/active
    ↓
RendererAdapter erzeugt sichtbare Textur/Layer
    ↓
DebugOverlay zeigt Metriken und Analysewerte
```

Wichtig:

```text
Die Engine zeichnet und nimmt Input an.
Der SimulationCore entscheidet, was physikalisch passiert.
```

---

## SimulationCore-Bezug

Das WorldCell-/WorldChunk-Modell ist das Datenfundament des `SimulationCore`.

Der SimulationCore braucht stabile Datenstrukturen, bevor entschieden wird, ob Godot, Unity, Bevy oder ein eigener Prototyp besser passt.

Wenn die Daten z. B. stark array-orientiert sind, profitieren Unity DOTS oder Rust/Bevy stärker.

Wenn schnelle Visualisierung, UI und Debugging wichtiger sind, kann Godot als erster Test trotzdem sinnvoll sein.

---

## Mögliche Speicherlayouts

### Array of Structs

```text
cells = [WorldCell, WorldCell, WorldCell, ...]
```

Vorteil:

- leicht verständlich
- jede Zelle enthält alles

Nachteil:

- bei vielen Zellen möglicherweise schlechter für Performance

### Struct of Arrays

```text
material_ids[]
phases[]
temperatures[]
velocity_x[]
velocity_y[]
masses[]
flags[]
```

Vorteil:

- oft besser für große Simulationen
- einzelne Felder können schneller gesammelt verarbeitet werden

Nachteil:

- weniger intuitiv
- Code wird abstrakter

### Vorläufige Empfehlung

Für die Dokumentation und erste Logik:

```text
Array of Structs denken.
```

Für Performance-Benchmarks später prüfen:

```text
Struct of Arrays oder chunkbasierte Hybridform.
```

---

## Beziehung zu Darstellungsschichten

Eine WorldCell ist Simulationsdaten.

Die Darstellung kann mehrere visuelle Layer daraus erzeugen:

| Layer | Datenquelle |
|---|---|
| Material-Layer | `material_id`, `phase` |
| Temperatur-Layer | `temperature` |
| Bewegungs-/Vektor-Layer | `velocity_x`, `velocity_y` |
| Analyse-Layer | `composition_ref`, Materialdaten |
| Zauber-Layer | aktive Effekte, Zielauswahl, Reichweite |
| UI/HUD | globale Metriken, FPS, Tickzeit |

Damit wird dieselbe Welt unterschiedlich sichtbar, ohne mehrere getrennte Welten zu benötigen.

---

## Warum dieses Modell vor der Engine-Wahl wichtig ist

Die Engine muss zu den Daten passen.

Wenn die Welt aus tausenden eigenständigen Figuren bestünde, wäre eine normale GameObject-/Node-Architektur plausibel.

Da die Welt aber aus sehr vielen kleinen Zellen besteht, braucht das Projekt eher:

- kompakte Datenarrays
- Chunking
- eigene Update-Logik
- Textur-/Buffer-basiertes Rendering
- Debug-Overlays
- Messbarkeit

Das ist eine andere Architektur als ein klassisches 2D-Jump'n'Run mit wenigen Sprites.

---

## Minimaler erster Prototyp

Für den ersten Benchmark genügt:

```text
WorldCell:
- material_id
- temperature
- velocity_x
- velocity_y
- flags

WorldChunk:
- cells[]
- active
- dirty
- total_mass
```

Materialien:

```text
0 = Luft
1 = Sand
2 = Wasser
3 = Stein
```

Erster Effekt:

```text
fallender Sand
oder
lokale Erwärmung mit Temperatur-Overlay
```

---

## Offene Fragen

1. Ist eine WorldCell ein sichtbarer Pixel, ein logischer Subpixel oder ein größerer Block?
2. Welche Chunkgröße ist sinnvoll: 16×16, 32×32, 64×64?
3. Werden Chunks immer rechteckig sein?
4. Wie werden Flüssigkeiten und Gase zwischen Chunks übertragen?
5. Wie werden Sub-Pixel-Fraktionen gespeichert?
6. Wie präzise müssen Masse und Energie pro Chunk bilanziert werden?
7. Wird die erste Simulation deterministisch sein?
8. Welche Daten gehören in Zellen und welche in Materialdefinitionen?
