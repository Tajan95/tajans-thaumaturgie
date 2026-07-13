# 16 — 2D World Simulation Model

**Stand:** 2026-07-14, 01:44 Europe/Berlin  
**Status:** Arbeitsmodell / Prototyping-Grundlage

Dieses Dokument sammelt frühe Entscheidungen und offene Fragen zur technischen Simulation der 2D-Welt.

Details zu Einheiten, Sub-Zell-Massen und numerischer Quantisierung siehe:

- `world_resolution_and_quantity_model.md`

---

## Ziel

Der erste Prototyp soll eine 2D-Seitenansicht simulieren, in der Materialien grundsätzlich:

- bewegbar
- zerstörbar
- transformierbar
- analysierbar
- trennbar
- thermisch und chemisch beeinflussbar

sind.

```text
x = horizontale Weltachse
y = vertikale Weltachse
z = keine kontinuierlich simulierte Raumachse
```

---

## Weltauflösung

Vorläufige Richtung:

```text
zellbasierte 2D-Welt
+ Sub-Zell-Positionen für starre Objekte
+ zellbasierter Fluss für Granulate, Flüssigkeiten und Gase
```

Das bedeutet:

- Die Welt besteht aus kleinen räumlichen Einheiten.
- Eine Zelle ist keine Mindestmasse und keine Mindeststoffmenge.
- Starre Objekte können sich mit kontinuierlicher oder Fixed-Point-Sub-Zell-Präzision bewegen.
- Flüssigkeiten, Gase und Granulate übertragen Masse, Impuls und Energie zwischen Zellen.
- Zellen speichern Temperatur, Materialfraktionen und lokale Zustände.

---

## Seitenansicht und diskrete Tiefenebenen

Der erste Prototyp verwendet eine Seitenansicht.

Optional können drei diskrete Tiefenebenen verwendet werden:

```text
Hintergrund
Hauptebene
Vordergrund
```

Diese Ebenen sind keine kontinuierliche 3D-Achse. Sie können als getrennte 2D-Raster mit expliziten Übergängen und Wechselwirkungen implementiert werden.

Noch offen ist, ob Hintergrund und Vordergrund physikalisch vollständig simuliert oder teilweise nur visuell verwendet werden.

---

## Pixel, Zellen und Materialfraktionen

Eine Weltzelle kann mehrere Informationen enthalten:

| Eigenschaft | Beispiel |
|---|---|
| Position | x/y-Koordinate + diskrete Tiefenebene |
| Hauptmaterial | Stein, Luft, Wasser |
| Materialfraktionen | N₂, O₂, CO₂ und Wasserdampf |
| Temperatur | 293 K |
| Phase | fest, flüssig, gasförmig, Plasma |
| Bewegungsvektor | Richtung + Geschwindigkeit |
| Druck / Dichte | optional |
| elektrische Ladung | optional |
| Zusammensetzungsreferenz | Verweis auf Sub-Zell-Massen |

---

## Sub-Zell-Fraktionen

Kleine Stoffanteile dürfen nicht verloren gehen, nur weil ihr Volumen kleiner als eine Zelle ist.

```text
sichtbare Zellgröße ≠ kleinste physikalische Stoffmenge
```

Eine Zelle kann mehrere Stoffmassen enthalten. Der Renderer zeigt eine dominante Materialklasse oder ein Gemisch, während die Simulation die Zusammensetzung erhält.

Beispiel:

```text
Luftzelle:
- Stickstoff
- Sauerstoff
- CO₂ in Spurmenge
- variabler Wasserdampf
```

Ein Trennzauber darf den CO₂-Anteil aus mehreren Zellen entfernen und in einer Zielzelle oder einem Behälter akkumulieren. Masse wird weder auf volle Zellen aufgerundet noch verworfen.

---

## Hierarchische Objektauflösung

Die Simulation verwendet die niedrigste Detailstufe, die für die aktuelle Interaktion ausreicht.

```text
stabiler Festkörper
→ aggregiertes RigidObject

lokale stoffliche Manipulation
→ Zell-/Komponentenauflösung

Bruch, Schmelzen oder Zerfall
→ Fragmente oder Flussmaterial
```

Eine Truhe kann daher als Gesamtobjekt bewegt werden. Erst das lokale Herauslösen ihrer Metallbeschläge erfordert eine detailliertere Materialauflösung.

---

## Bewegungsmodelle

### Starre Objekte

```text
Sub-Zell-Position
+ kontinuierliche Geschwindigkeit
+ kontinuierliche Rotation
+ rasterisierte Belegung / Kollision
```

Dadurch bleiben langsame und gekrümmte Bewegungen möglich, ohne die zellbasierte Welt aufzugeben.

### Sand und andere Granulate

```text
zellbasierter Transfer
+ Ruhe-/Rutschregeln
+ optionaler Impulstransport
```

### Flüssigkeiten

```text
zellbasierter Massen-, Druck- und Impulstransfer
```

### Gase

```text
zellbasierter Stoffmengen-, Druck-, Wärme- und Diffusionstransfer
```

---

## Ruhende Objekte

Ruhende oder sehr langsame starre Objekte können später optional in eine stabile Rasterbelegung einrasten.

Restenergie oder Bilanzdifferenzen dürfen dabei nicht stillschweigend verschwinden. Sie werden bevorzugt als Reibungswärme oder numerisches Residuum verbucht.

Globale Energieflüsse durch Sonne, Erdwärme oder Abstrahlung existieren unabhängig davon und sollen numerische Fehler nicht kaschieren.

---

## Physikalische und numerische Größen

Die Welt verwendet SI-kompatible Größen.

Vorläufige Arbeits- und Anzeigeeinheiten:

- Meter
- Gramm
- Sekunde
- Kelvin
- Joule
- Newton
- Watt

Ein Joule ist die semantische Energieeinheit, nicht zwingend die kleinste numerische Energiemenge.

Vorläufige Implementationshypothese:

```text
Fixed-Point-Integer
+ Energiequantum kleiner als 1 J
+ erster Benchmark mit Millijoule
```

---

## Hierarchische Material- und Wärmeverteilung

Wärme, Gase, Flüssigkeiten und feine Partikel sollen nicht überall auf maximaler Detailstufe simuliert werden.

```text
lokal präzise → regional aggregiert → global bilanziert
```

### Beispiel: Abwärme

1. Direkt am Effektort wird Abwärme präzise berechnet.
2. In mittlerer Entfernung wird sie gröber auf Bereiche verteilt.
3. In großer Entfernung wird sie als regionaler oder globaler Wärmebeitrag bilanziert.

### Beispiel: CO₂

- In einem geschlossenen Raum bleibt CO₂ lokal oder regional erhalten.
- Im Freien kann es später in einen atmosphärischen Aggregatwert übergehen.
- Masse darf dabei nicht verschwinden.

---

## Erhaltungsprüfer

| Prüfer | Aufgabe |
|---|---|
| Massenbilanz | Prüft Material- und Komponentenmasse. |
| Energiebilanz | Prüft Wärme, Arbeit, Verluste und numerische Residuen. |
| Impulsbilanz | Prüft Bewegungsänderungen und Gegenimpulse. |
| Containerprüfung | Erkennt geschlossene Räume und Behälter. |
| Fraktionsprüfung | Prüft Sub-Zell-Anteile und Aggregation. |
| Reaktionsprüfung | Prüft chemische und nukleare Umwandlungen. |

---

## Performance-Risiken

Problematische Fälle:

- Explosionen
- viele bewegte Zellen oder Fragmente
- viele Kollisionen
- gleichzeitige Transformationen
- Gas- und Flüssigkeitsdiffusion
- Wärmeausbreitung
- Feuer und Plasma
- chemische Kettenreaktionen
- viele individuelle Stoffkomponenten pro Zelle
- häufige Live-Zielabfragen von Zaubern

---

## Mögliche Optimierungsansätze

| Ansatz | Zweck |
|---|---|
| Chunking | Welt in größere Berechnungsbereiche teilen. |
| Spatial Partitioning | Kollisionen lokal prüfen. |
| LOD-Aggregation | entfernte oder kleine Effekte gröber berechnen. |
| Aktivitätsmasken | nur aktive Bereiche aktualisieren. |
| Ereignisbasierte Updates | nur bei Änderungen neu berechnen. |
| Fixed-Point-Quantisierung | reproduzierbare Mengen- und Energiebilanzen. |
| CompositionPool | komplexe Mischungen außerhalb der Zellen speichern. |
| Schlafende Objekte | ruhende Materialien nicht ständig simulieren. |
| Container-Regionen | Räume und Behälter als Bilanzräume behandeln. |

---

## Bezug zur Zaubersyntax

Zauber können auf verschiedenen Auflösungsebenen wirken:

```text
ObjectRef
CellRef
CellRegionRef
SurfaceRef
MaterialFractionRef
LayerRef
```

Beispiele:

```text
Bewege den Stein
→ ObjectRef + ApplyForce

Erhitze eine lokale Steinfläche
→ CellRegionRef oder SurfaceRef + TransferThermalEnergy

Trenne CO₂ aus Luft
→ MaterialFractionRef + TransportComponentMass
```

---

## Offene Fragen

1. Welche Zellbreite und Zellhöhe trägt der erste Prototyp?
2. Welche angenommene Tiefe besitzt eine 2D-Ebene?
3. Sind Hintergrund und Vordergrund physikalisch oder teilweise nur visuell?
4. Welche Cross-Layer-Wechselwirkungen werden erlaubt?
5. Welche Fixed-Point-Quanten werden für Masse, Energie und Position gewählt?
6. Wie werden Bewegungsvektoren und Kollisionen performant berechnet?
7. Welche Stoffe werden lokal präzise simuliert und welche aggregiert?
8. Wie erkennt das System geschlossene Räume und Container?
9. Welche Ereignisse erzwingen höhere Simulationsauflösung?
10. Wie werden Explosionen begrenzt, ohne Erhaltungssätze zu brechen?
