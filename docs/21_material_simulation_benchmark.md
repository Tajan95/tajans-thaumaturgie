# 21 — Material Simulation Benchmark

Dieses Dokument definiert einen ersten technischen Benchmark für die 2D-Materialsimulation.

**Status:** Arbeitsmodell / Prototyping-Plan

---

## Zweck

Der Benchmark soll herausfinden, ob eine Engine oder ein Framework die geplante Weltarchitektur praktisch tragen kann.

Nicht getestet wird zuerst ein vollständiges Spiel.

Getestet wird:

```text
Kann die technische Basis viele Weltzellen verwalten, anzeigen und verändern?
```

---

## Beziehung zur Engine-Entscheidung

Die Engine-Entscheidung sollte nicht nur nach Bauchgefühl getroffen werden.

Stattdessen:

```text
1. Datenmodell definieren
2. Minimal-Benchmark festlegen
3. Kandidaten praktisch testen
4. Engine-Entscheidung dokumentieren
```

Relevante Issues:

- #15 — Minimalen Engine-Benchmark definieren
- #21 — Erste Engine/Framework auswählen
- #23 — Datenmodell für Weltzellen und Chunks skizzieren

---

## Was der Benchmark beantworten soll

### Hauptfragen

1. Wie viele Weltzellen können stabil dargestellt werden?
2. Wie teuer ist ein einfacher Simulationstick?
3. Wie gut lassen sich mehrere Darstellungsschichten anzeigen?
4. Wie sauber kann Simulation von Rendering getrennt werden?
5. Wie gut lassen sich Debugwerte messen?
6. Wie schwer ist es, Materialzustände sichtbar zu machen?

### Nicht-Ziele

Der Benchmark soll zunächst nicht testen:

- vollständige Zaubersyntax
- komplexe Chemie
- vollständige Flüssigkeitssimulation
- vollständige Gasdynamik
- KI/LLM-Zaubercompiler
- fertiges Gameplay
- Steam-Export

---

## Minimaler Testumfang

### Weltgröße

Mehrere Stufen:

| Stufe | Raster | Zellzahl | Zweck |
|---|---:|---:|---|
| A | 128 × 128 | 16.384 | Einstieg / Debug |
| B | 316 × 316 | ca. 100.000 | erster realistischer Benchmark |
| C | 512 × 512 | 262.144 | mittlere Last |
| D | 1000 × 1000 | 1.000.000 | obere Zielspanne |

### Materialien

Erste Materialien:

| ID | Material | Zweck |
|---|---|---|
| 0 | Luft | Hintergrund / leerer Raum |
| 1 | Sand | einfache Gravitation / Bewegung |
| 2 | Wasser | Flüssigkeitstest später |
| 3 | Stein | statisches Hindernis |
| 4 | Wärmequelle | Debug-/Temperaturtest |

Für den ersten Test reichen Luft, Sand und Stein.

---

## Benchmark-Phase 1 — Daten ohne Engine

Optional, aber sehr sinnvoll.

Ziel:

```text
Kann das WorldCell-/WorldChunk-Modell unabhängig von einer Engine logisch simulieren?
```

Test:

- Zellarray erzeugen
- Material setzen
- einfachen Tick berechnen
- aktive Zellen zählen
- Masse prüfen
- Laufzeit messen

Vorteil:

Ein solcher Test kann später in Godot, Unity oder Bevy eingebunden werden.

---

## Benchmark-Phase 2 — Darstellung

Ziel:

```text
Kann die Engine das Zellraster performant sichtbar machen?
```

Test:

- Raster erzeugen
- Materialfarben anzeigen
- Bild/Textur pro Tick aktualisieren
- Kamera/Zoom optional
- FPS messen

Wichtig:

```text
Keine Zelle als einzelner Engine-Node / GameObject.
```

Das Raster soll über Textur, Buffer, Tilemap oder vergleichbare Technik dargestellt werden.

---

## Benchmark-Phase 3 — Darstellungsschichten

Ziel:

```text
Kann die Engine mehrere 2D-Schichten sinnvoll trennen?
```

Mindestschichten:

| Layer | Inhalt |
|---|---|
| Material-Layer | sichtbare Weltzellen |
| Debug-/Analyse-Layer | Temperatur, Vektoren, Zielradius |
| UI/HUD-Layer | FPS, Tickzeit, Zellzahl |

Test:

- Overlay an/aus schalten
- Temperatur oder Vektoren anzeigen
- HUD bleibt unabhängig von Weltkamera lesbar

---

## Benchmark-Phase 4 — Einfache Simulation

Erster geeigneter Testfall:

```text
fallender Sand
```

Warum?

- leicht sichtbar
- nutzt Nachbarzellen
- zeigt aktive Zellen
- testet Update-Reihenfolge
- testet Performance vieler kleiner Bewegungen

Regelidee:

```text
Wenn Zelle Sand ist:
    wenn Zelle darunter Luft ist → tauschen
    sonst wenn diagonal unten frei → tauschen
    sonst ruhen
```

Optionaler zweiter Test:

```text
lokale Erwärmung + Temperatur-Overlay
```

Warum?

- testet Zustandswerte ohne Materialbewegung
- zeigt Debug-Overlay
- bereitet Wärme-/Energiefragen vor

---

## Benchmark-Phase 5 — Mini-Zaubereffekt

Noch keine echte Zaubersyntax.

Nur ein harter Testeffekt:

```text
Mausklick erzeugt lokalen Effekt in Radius r
```

Mögliche Effekte:

| Effekt | Zweck |
|---|---|
| Sand erzeugen | Materialsetzung testen |
| Stein löschen | Materialänderung testen |
| Hitze setzen | Temperaturfeld testen |
| Explosion | viele Bewegungsvektoren testen |
| Materialanalyse | Overlay/Fraktionen testen |

Für den ersten Durchlauf:

```text
Mausklick setzt Sand oder Wärme.
```

Explosionen erst später.

---

## Zu messende Metriken

Mindestmetriken:

| Metrik | Bedeutung |
|---|---|
| FPS | sichtbare Bildrate |
| Simulationszeit pro Tick | Kosten der Weltlogik |
| Renderzeit | Kosten der Darstellung |
| Zellzahl | Gesamtzahl der Zellen |
| aktive Zellzahl | tatsächlich aktualisierte Zellen |
| aktive Chunkzahl | Chunks, die simuliert werden |
| Dirty-Chunkzahl | Chunks, deren Darstellung neu erzeugt wird |
| Massenbilanz | ob Material verloren geht |

Optional später:

- Speicherverbrauch
- Energie-/Temperaturbilanz
- Anzahl bewegter Zellen
- Kollisionszahl
- Updatezeit pro Chunk

---

## Erfolgskriterien

Ein erster Benchmark gilt als erfolgreich, wenn:

- ein Zellraster sichtbar ist
- mindestens 100.000 Zellen darstellbar sind
- ein einfacher Sand- oder Wärmetest stabil läuft
- FPS, Tickzeit und Zellzahl sichtbar sind
- Simulation und Rendering logisch getrennt bleiben
- mehrere Layer/Overlays grundsätzlich funktionieren
- die Architektur nicht direkt an einzelne Engine-Objekte pro Zelle gebunden ist

## Warnsignale

Warnsignale für eine Engine oder Architektur:

- viele Zellen müssen als einzelne Engine-Objekte erzeugt werden
- Debugging einfacher Zustände ist schwer
- Rasteraktualisierung ist bereits bei 100.000 Zellen zu langsam
- Layer/Overlays sind umständlich
- Simulationsdaten sind eng an Engine-spezifische Objekte gebunden
- Messwerte lassen sich nicht sauber anzeigen

## Abbruchkriterien

Ein Ansatz sollte verworfen oder stark überarbeitet werden, wenn:

- 100.000 Zellen mit einfachem Update nicht sinnvoll laufen
- Darstellung und Simulation nicht trennbar bleiben
- einfache Debug-Metriken nicht praktikabel sind
- die Implementierung schon für fallenden Sand unverhältnismäßig komplex wird

---

## Kandidaten-neutraler Ablauf

Der Benchmark sollte so formuliert sein, dass er mit verschiedenen Kandidaten durchgeführt werden kann.

| Schritt | Godot | Unity DOTS | Bevy/Rust | Custom Mini |
|---|---|---|---|---|
| Datenmodell | Array/Resource/Script | ECS/NativeArray | ECS/Vec/Resources | freie Struktur |
| Darstellung | Image/Texture/Canvas | Texture2D/RenderTexture | Texture/Render pipeline | einfache Canvas/SDL/etc. |
| Overlay | CanvasLayer/UI | UI/Debug Draw | egui/bevy_ui | eigener Overlay |
| Performance | GDScript/C#/GDExtension | Burst/Jobs | Rust native | abhängig |

Dadurch bleibt der Test fairer und nicht automatisch Godot-zentriert.

---

## Vorläufige Reihenfolge

Empfohlene nächste Schritte:

1. Datenmodell aus `docs/20_world_cell_and_chunk_model.md` auf Minimalform reduzieren.
2. Benchmark-Testfall festlegen: fallender Sand + HUD-Metriken.
3. Eine Kandidatenumgebung auswählen.
4. Benchmark implementieren.
5. Ergebnisse dokumentieren.
6. Erst danach Engine-Entscheidung treffen.

## Aktuelle Empfehlung

Nicht sofort endgültig Godot wählen.

Besser:

```text
Engine-Entscheidung nach einem kleinen Benchmark treffen.
```

Wenn schnell sichtbare Ergebnisse Priorität haben, ist Godot ein plausibler erster Testkandidat.

Wenn reine Simulationsperformance und datenorientierte Architektur Priorität haben, sollten Unity DOTS oder Bevy/Rust gleichberechtigt geprüft werden.

Da KI-Tools einen Teil der Implementierung übernehmen können, ist persönlicher Lernaufwand weniger wichtig als:

- Architekturpassung
- Debuggability
- Messbarkeit
- langfristige Erweiterbarkeit
- Trennung von Simulation und Darstellung

---

## Offene Fragen

1. Welcher Kandidat wird zuerst getestet?
2. Soll der erste Benchmark engine-neutral als kleiner Konsolen-/Python-/Rust-Test beginnen?
3. Ist fallender Sand der richtige erste Testfall?
4. Soll Temperatur direkt im ersten Benchmark enthalten sein?
5. Welche Zellzahl ist das Mindestziel für eine positive Bewertung?
6. Wie stark soll Noita als technische Referenz dienen?
7. Welche Ergebnisse müssen dokumentiert werden, bevor #21 entschieden wird?
