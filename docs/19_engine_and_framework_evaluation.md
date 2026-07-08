# 19 — Engine and Framework Evaluation

Dieses Dokument sammelt Anforderungen und erste Bewertungsannahmen für die technische Umsetzung des 2D-Prototyps.

**Status:** Arbeitsdokument / technische Vorentscheidung offen

---

## Ziel dieses Dokuments

Die Engine-Frage soll nicht ad hoc entschieden werden. Zuerst werden Anforderungen, Risiken und Testfälle definiert. Danach kann eine erste Engine-Sandbox begründet ausgewählt werden.

Der Fokus liegt nicht auf „Welche Engine kann alles?“, sondern auf:

```text
Welche Engine oder welches Framework trägt unsere spezifische 2D-Materialsimulation am besten?
```

---

## Grundannahme

Die Engine soll nicht die eigentliche Weltphysik hardcoden.

Stattdessen gilt vorläufig:

```text
SimulationCore = eigene regelbasierte Material- und Magiesimulation
Engine = Darstellung, Input, UI, Debugging, Tooling, Export/Packaging
```

Dadurch bleibt das Projekt langfristig weniger abhängig von einer einzelnen Engine.

---

## Referenz: Noita

Noita ist eine wichtige technische Referenz, weil es zeigt, dass eine 2D-Welt mit stark material-/pixelbasierter Simulation spielerisch tragfähig sein kann.

Relevante Aspekte:

- große Mengen simulierter 2D-Materie
- zerstörbare Umgebung
- Materialreaktionen
- emergente Wechselwirkungen
- starke Lesbarkeit durch einfache visuelle Zustände
- interessante Fehler- und Kettenreaktionen

Abgrenzung:

Tajan's Thaumaturgie soll keine Noita-Kopie werden. Der Hauptunterschied liegt im Magiesystem:

```text
Noita: viele feste Zauber/Projektile + emergente Materialwelt
Tajan's Thaumaturgie: formal ableitbare Zaubersyntax + materialbasierte Welt
```

Noita ist also primär technische und systemische Inspiration, nicht strukturelles Designziel.

---

## Zielbild des 2D-Prototyps

Der erste Prototyp soll eine kleine 2D-Welt darstellen, in der Zellen oder Pixel Materialzustände tragen.

Mindestidee:

```text
Weltzelle = Material + Phase + Temperatur + Bewegungsvektor + optionale Fraktionen
```

Beispiele für frühe Tests:

- fallender Sand
- Wasser erhitzen/abkühlen
- einfache Luft-/Gasverteilung
- Materialanalyse
- Temperatur-Overlay
- einfache Explosion
- Materialtrennung
- Masse-/Energiebilanzanzeige

---

## Darstellungsschichten

Die 2D-Welt soll nicht nur eine einzige flache Ebene besitzen. Mindestens zwei, wahrscheinlich drei Schichten sind sinnvoll.

| Schicht | Zweck | Simulation oder Darstellung? |
|---|---|---|
| Material-Layer | sichtbare Weltmaterie: Sand, Stein, Wasser, Luft, Objekte | Simulation + Darstellung |
| Zauber-/Analyse-/Debug-Layer | Zielradien, Vektoren, Temperatur, Materialanalyse, Zauberstruktur | primär Darstellung, teils Simulation |
| UI/HUD-Layer | Metriken, Inventar, Makros, FPS, Mana/Kosten | Darstellung |

Optional könnte später eine Pseudo-3D- oder Tiefenschicht entstehen:

```text
Vordergrund / Materialebene / Hintergrund
```

oder:

```text
materielle Ebene / Analyseebene / Interfaceebene
```

Wichtig: Mehrere Darstellungsschichten bedeuten nicht automatisch mehrere getrennte Simulationswelten.

---

## Funktionale Anforderungen

### Muss-Anforderungen

| ID | Anforderung |
|---|---|
| F-001 | 2D-Welt mit vielen kleinen Zellen/Pixels darstellen können |
| F-002 | eigene Materialdaten pro Zelle verwalten können |
| F-003 | Weltzustand pro Tick aktualisieren können |
| F-004 | mehrere visuelle Schichten/Overlays darstellen können |
| F-005 | Debug-Overlay mit FPS, Zellzahl und Updatezeit ermöglichen |
| F-006 | Input für einfache Interaktion ermöglichen, z. B. Material setzen, Effekt auslösen |
| F-007 | eigenes Rendering für Zellraster oder Textur-Buffer ermöglichen |
| F-008 | Projekt sauber mit GitHub versionierbar halten |
| F-009 | Windows-Export grundsätzlich ermöglichen |

### Sollte-Anforderungen

| ID | Anforderung |
|---|---|
| S-001 | später native Erweiterungen erlauben, z. B. C++, Rust oder C#-Jobs |
| S-002 | GPU-/Compute-Experimente ermöglichen |
| S-003 | einfache UI und Editor-nahe Debugtools unterstützen |
| S-004 | spätere 3D-Experimente nicht grundsätzlich blockieren |
| S-005 | ausreichend gute Profiling- und Debugging-Möglichkeiten bieten |
| S-006 | Steam-Veröffentlichung perspektivisch nicht unnötig erschweren |

### Kann-Anforderungen

| ID | Anforderung |
|---|---|
| K-001 | integrierter Level-Editor |
| K-002 | Hot Reloading oder schnelle Iterationszyklen |
| K-003 | Community-Plugins für Debugging/Profiling |
| K-004 | Web-Export für kleine Demos |
| K-005 | spätere Controller-Unterstützung |

---

## Nicht-funktionale Anforderungen

Die konkreten Zielwerte sind vorläufig und müssen im Benchmark überprüft werden.

| ID | Anforderung | Vorläufiger Zielwert |
|---|---|---|
| NF-001 | stabile Darstellung | 60 FPS bei kleinen bis mittleren Szenen |
| NF-002 | Simulations-Tickzeit | sichtbar messbar, Ziel < 16 ms für einfache Tests |
| NF-003 | Zellzahl erster Test | 100.000 bis 1.000.000 Zellen als Benchmark-Spanne |
| NF-004 | Debuggability | Zustände müssen sichtbar und messbar sein |
| NF-005 | Architektur | Simulation und Rendering müssen trennbar bleiben |
| NF-006 | Reproduzierbarkeit | Testläufe sollen möglichst deterministisch oder protokollierbar sein |
| NF-007 | Erweiterbarkeit | Materialattribute und Zauberkomponenten müssen modular erweiterbar sein |
| NF-008 | Lernaufwand | erster sichtbarer Prototyp soll ohne monatelange Engine-Einarbeitung möglich sein |

---

## Architekturhypothese

Der Simulationskern sollte nicht aus tausenden Engine-Objekten bestehen.

Stattdessen:

```text
WorldCell[] / ChunkData[]  →  SimulationCore  →  Texture/Buffer/RendererAdapter
```

### Vorläufige Komponenten

| Komponente | Aufgabe |
|---|---|
| SimulationCore | Zellzustände, Materialregeln, Wärme, Bewegung, Erhaltung |
| RendererAdapter | übersetzt Zellzustand in sichtbare Darstellung |
| InputAdapter | nimmt Spieleraktionen/Debugbefehle entgegen |
| DebugOverlay | zeigt Metriken und Analyseansichten |
| SpellSystem | erzeugt Zustandsänderungen über Zauberlogik |
| GameLoop | koordiniert Tick, Rendering und Input |

### Wichtige Architekturregel

```text
Keine Weltzelle als einzelner Engine-Node / GameObject / Entity, solange nicht bewiesen ist, dass das performant bleibt.
```

Die Weltzellen sollten primär als kompakte Datenarrays oder Chunks modelliert werden.

---

## CPU-first vs. GPU-first

Für den ersten Prototyp wird eine CPU-first-Strategie empfohlen.

### CPU-first für frühe Tests

- Zellzustände
- einfache Bewegung
- Temperaturupdates
- Fraktionen
- Materialanalyse
- Debug-Bilanzen
- deterministische Testfälle

### GPU/Compute später prüfen für

- sehr große Zellmengen
- Wärme-/Diffusionsfelder
- parallele Zellupdates
- große Vektorfelder
- Rendering sehr großer Materialkarten

### Grund

CPU-first ist leichter zu debuggen. GPU/Compute kann später wichtig werden, erhöht aber Komplexität, Debugging-Aufwand und Datenübertragungsprobleme.

---

## Kandidaten

### Option A — Godot-first

Godot ist ein guter Kandidat für den ersten sichtbaren 2D-Prototyp.

#### Stärken

- starker 2D-Fokus
- schneller Einstieg mit Editor, Szenen, Nodes und GDScript
- gut für visuelle Debug-Overlays und UI
- mehrere 2D-Darstellungsschichten über CanvasLayer möglich
- Open Source / keine Lizenzkosten
- C# und C++/GDExtension als spätere Eskalationspfade
- Compute Shader grundsätzlich möglich

#### Risiken

- keine vorhandene Projekterfahrung
- sehr große Zellwelten dürfen nicht naiv als einzelne Nodes umgesetzt werden
- schwere Simulation muss wahrscheinlich als eigener Datenkern laufen
- Compute Shader erhöhen Komplexität und sind nicht der richtige erste Schritt

#### Einschätzung

Godot ist wahrscheinlich der beste erste Kandidat, wenn wir ihn als **Visualisierungs- und Sandbox-Engine** nutzen, nicht als fertige Physiklösung.

```text
Godot = erster sichtbarer Prototyp / Editor / UI / Layer / Debugging
Simulation = eigener datenorientierter Kern
```

### Keine Godot-Erfahrung: Risiko und Umgang

Keine Vorerfahrung ist ein echtes, aber begrenzbares Risiko.

Für den ersten Test muss nicht „Godot vollständig gelernt“ werden. Der Minimalpfad ist:

1. Projekt anlegen.
2. einfache 2D-Szene öffnen.
3. Script an Node hängen.
4. Pixelraster oder Textur anzeigen.
5. Input auslesen.
6. Debug-Text/FPS anzeigen.
7. zweite Darstellungsschicht testen.

Komplexe Godot-Features werden zunächst bewusst vermieden.

---

### Option B — Unity DOTS / ECS

Unity DOTS ist technisch attraktiv für datenorientierte, große Simulationen.

#### Stärken

- datenorientiertes ECS-Modell
- Burst Compiler und C# Job System für Performance
- etablierte Engine und Toolchain
- große Community
- gute kommerzielle/Steam-Tauglichkeit
- später 2D und 3D möglich

#### Risiken

- höherer Einstiegsoverhead
- Unity-Ökosystem ist komplexer
- DOTS/ECS ist für Anfänger weniger direkt sichtbar als Godot
- stärkerer Engine-/Ökosystem-Lock-in
- Lizenz-/Geschäftsmodell muss im Blick bleiben

#### Einschätzung

Unity DOTS ist wahrscheinlich der stärkste Kandidat für einen performanten datenorientierten Ansatz, aber nicht zwingend der beste erste Lern- und Explorationsschritt.

---

### Option C — Bevy / Rust

Bevy ist ein datengetriebenes Rust-Engine-Projekt mit ECS-Fokus.

#### Stärken

- Rust und ECS passen gut zu einem eigenen Simulationskern
- sehr gute Kontrolle über Datenstrukturen
- freie/open-source Lizenzierung
- moderne 2D-/3D-Rendering-Basis
- natürliche Nähe zu datenorientierter Architektur

#### Risiken

- weniger „fertiger Editor“ als Godot oder Unity
- mehr Eigenbau für Tools, UI und Debugging
- Rust-Lern-/Build-/Architekturaufwand
- weniger anfängerfreundlich für schnelle visuelle Ergebnisse

#### Einschätzung

Bevy ist interessant, wenn Simulation und Datenmodell wichtiger werden als Editor-Komfort. Für den allerersten sichtbaren Prototyp wirkt es aber weniger niedrigschwellig als Godot.

---

### Option D — Eigener Minimal-Prototyp

Ein eigener Minimal-Prototyp, z. B. in Python, JavaScript, C#, C++ oder Rust, könnte den Simulationskern extrem klar testen.

#### Stärken

- maximale Kontrolle
- kein Engine-Lock-in
- gut für isolierte Benchmarks
- einfache Datenmodell-Experimente

#### Risiken

- Darstellung, UI, Input, Export und Tooling müssen selbst gebaut werden
- Gefahr, zu viel Infrastruktur vor dem eigentlichen System zu schreiben
- weniger motivierend als sichtbare Engine-Sandbox

#### Einschätzung

Sehr gut für isolierte Simulationstests, aber nicht als alleinige erste Spiel-Engine-Strategie.

---

## Bewertungsmatrix

Skala: 1 = schwach, 5 = stark. Vorläufige Einschätzung, noch nicht benchmark-basiert.

| Kriterium | Godot | Unity DOTS | Bevy/Rust | Custom Mini |
|---|---:|---:|---:|---:|
| schneller sichtbarer 2D-Prototyp | 5 | 3 | 3 | 2 |
| Lernaufwand für ersten Test | 4 | 2 | 2 | 3 |
| datenorientierte Simulation | 3 | 5 | 5 | 5 |
| 2D-Layer/Overlays | 5 | 4 | 3 | 2 |
| UI/Debugging schnell | 5 | 4 | 3 | 2 |
| Performance-Potenzial | 3–4 | 5 | 4–5 | abhängig |
| native Erweiterbarkeit | 4 | 4 | 5 | 5 |
| GPU/Compute-Pfad | 3–4 | 4 | 4 | abhängig |
| GitHub-freundlich | 5 | 4 | 5 | 5 |
| spätere 3D-Option | 4 | 5 | 4 | abhängig |
| Steam-Perspektive | 4 | 5 | 3–4 | abhängig |
| Engine-Lock-in gering | 4, wenn Kern getrennt | 2–3 | 4 | 5 |

## Vorläufige Empfehlung

```text
Godot-first als Hypothese testen.
```

Aber nicht als finale Engine-Entscheidung.

Begründung:

- Wir brauchen schnell sichtbare 2D-Ergebnisse.
- Godot wirkt für Layer, UI, Debugging und 2D-Sandbox sehr geeignet.
- Fehlende Godot-Erfahrung ist ein beherrschbares Lernrisiko.
- Der Simulationskern soll engine-neutral bleiben.
- Wenn Godot beim Benchmark scheitert, bleiben Unity DOTS und Bevy/Rust als nächste Kandidaten.

---

## Minimaler Engine-Benchmark

Der erste Benchmark soll keine vollständige Spielmechanik enthalten.

### Testumfang

```text
Zellraster: 316 × 316 bis 1000 × 1000
Zellen: ca. 100.000 bis 1.000.000
Materialien: 4–8
Schichten: Material + Overlay + UI
Effekte: Bewegung, Temperatur, einfache Explosion oder Materialtrennung
Metriken: FPS, Tickzeit, Zellzahl, aktive Zellen, Speicher grob
```

### Erfolgskriterien

- Zellraster sichtbar und interaktiv.
- zweites Overlay kann ein- und ausgeschaltet werden.
- UI zeigt Metriken.
- einfacher Simulationstick läuft stabil.
- Datenmodell bleibt getrennt von Darstellung.
- keine Zelle wird als einzelner Node/GameObject modelliert.

### Abbruchkriterien

- Darstellung großer Zellmengen ist zu langsam.
- Debugging wird unübersichtlich.
- Datenmodell lässt sich nicht sauber von Engine-Strukturen trennen.
- Layer/Overlays werden zu umständlich.
- Lernaufwand blockiert Fortschritt unverhältnismäßig.

---

## Erste Sandbox-Ziele für Godot

Falls Godot zuerst getestet wird:

```text
prototype/2d/godot_sandbox/
```

Minimalziel:

1. 2D-Szene erstellen.
2. Materialraster als Textur oder ImageBuffer anzeigen.
3. CanvasLayer für Debug/HUD testen.
4. Eingabe: Maus setzt Material oder löst Effekt aus.
5. Simulationskern als Array/Chunk-Datenstruktur.
6. FPS/Tickzeit/Zellzahl anzeigen.
7. Testeffekt: fallender Sand oder Wärmeausbreitung.

---

## Offene Fragen

1. Wird die 2D-Welt Seitenansicht, Top-Down oder Hybrid?
2. Welche drei Darstellungsschichten sind für den ersten Test wirklich nötig?
3. Welche Zellzahl ist realistisch für einen ersten Benchmark?
4. Reicht GDScript für den ersten Test, oder sollte C# direkt genutzt werden?
5. Wann wird GDExtension/C++ relevant?
6. Wann wird GPU/Compute relevant?
7. Soll Unity DOTS parallel oder erst nach Godot getestet werden?
8. Ist Bevy/Rust als späterer Simulationskern-Kandidat relevant?
9. Wie eng soll der erste Prototyp an Noita als technische Referenz angelehnt sein?

---

## Verknüpfte Issues

- #9 — Technik: Game Engine für 2D-Prototyp und spätere 3D-/Steam-Tauglichkeit prüfen
- #15 — Prototyp: Minimalen Engine-Benchmark für Materialsimulation definieren
- #16 — Architektur: Darstellungsschichten der 2D-Welt definieren
- #17 — Lernpfad: Godot-Grundlagen für ersten 2D-Prototyp prüfen
- #18 — Referenzanalyse: Noita als technische und systemische Vergleichsbasis auswerten
- #19 — Architektur: Simulationskern von Engine-Darstellung trennen
- #20 — Feature: Debug- und Analyse-Overlays für Materialwelt planen
- #21 — Entscheidung: Erste Engine/Framework für Prototyp auswählen

---

## Quellen / technische Referenzen

- Godot Docs — Compute Shaders: https://docs.godotengine.org/en/stable/tutorials/shaders/compute_shaders.html
- Godot Docs — GDExtension: https://docs.godotengine.org/en/stable/tutorials/scripting/gdextension/index.html
- Godot Docs — CanvasLayer: https://docs.godotengine.org/en/stable/classes/class_canvaslayer.html
- Unity — DOTS: https://unity.com/dots
- Unity Docs — Entities overview: https://docs.unity3d.com/Packages/com.unity.entities@1.3/manual/index.html
- Bevy: https://bevy.org/
