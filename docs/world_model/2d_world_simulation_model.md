# 16 — 2D World Simulation Model

Dieses Dokument sammelt frühe Entscheidungen und offene Fragen zur technischen Simulation der 2D-Welt.

**Status:** Arbeitsmodell / Prototyping-Fragen

---

## Ziel

Der erste Prototyp soll eine 2D-Welt simulieren, in der Materialien grundsätzlich:

- bewegbar
- zerstörbar
- transformierbar
- analysierbar
- trennbar
- thermisch und chemisch beeinflussbar

sind.

## Weltauflösung

Vorläufige Wunschrichtung:

```text
pixel-/zellbasierte 2D-Welt + flüssige Bewegungsvektoren
```

Das bedeutet:

- Die Welt besteht aus kleinen räumlichen Einheiten.
- Materialien können sich in diesen Einheiten befinden.
- Bewegung ist nicht nur grob entlang x/y-Achsen möglich.
- Zellen/Pixel können Vektoren, Temperatur, Materialfraktionen und Zustand speichern.

## Pixel, Zellen und Materialfraktionen

Eine Weltzelle kann mehrere Informationen enthalten:

| Eigenschaft | Beispiel |
|---|---|
| Position | x/y-Koordinate |
| Hauptmaterial | Stein, Luft, Wasser |
| Materialfraktionen | 78% N₂, 21% O₂, Rest |
| Temperatur | 293 K |
| Phase | fest, flüssig, gasförmig, Plasma |
| Bewegungsvektor | Richtung + Geschwindigkeit |
| Druck / Dichte | optional |
| elektrische Ladung | optional |
| Magnetfeldwert | optional |

## Sub-Pixel-Fraktionen

Kleine Stoffanteile dürfen nicht verloren gehen, nur weil ihr Volumen kleiner als ein Pixel wäre.

Arbeitsmodell:

```text
Fraktionen unter 1 Pixelvolumen können denselben Zellraum überlagern,
solange ihre Summe unterhalb definierter Schwellen bleibt.
```

Beispiel:

Wenn Gestein 0,4% Gold und 0,2% Platin enthält, können diese Fraktionen bei Analyse oder Trennung sichtbar werden, ohne sofort realistisch große Pixelvolumina zu erzwingen.

### Offene technische Frage

Wie werden solche Fraktionen behandelt, wenn sie:

- getrennt werden
- bewegt werden
- kollidieren
- konzentriert werden
- über mehrere Zellen aggregiert werden?

## Hierarchische Material- und Wärmeverteilung

Wärme, Gase, Flüssigkeiten und feine Partikel sollen nicht auf unendlich detaillierter Ebene simuliert werden.

Stattdessen wird ein hierarchisches Modell vorgeschlagen:

```text
lokal präzise → regional aggregiert → global bilanziert
```

### Beispiel: Abwärme

1. Direkt am Effektort wird Abwärme präzise berechnet.
2. In mittlerer Entfernung wird sie gröber auf Bereiche verteilt.
3. In großer Entfernung wird sie als globaler oder regionaler Wärmebeitrag bilanziert.

### Beispiel: CO₂-Erzeugung

Ein Zauber oder eine Maschine produziert CO₂.

- In einem geschlossenen Raum muss CO₂ lokal/regional erhalten bleiben.
- Im Freien kann es ab einer gewissen Entfernung in einen atmosphärischen Aggregatwert übergehen.
- Masse darf dabei nicht verschwinden.

## Erhaltungsprüfer

Damit Optimierungen nicht Massen- oder Energieerhaltung brechen, braucht die Simulation Prüfer.

Mögliche Prüfer:

| Prüfer | Aufgabe |
|---|---|
| Massenbilanz | Prüft, ob Materialmenge erhalten bleibt. |
| Energiebilanz | Prüft Wärme, Arbeit und Verluste. |
| Impulsbilanz | Prüft Bewegungsänderungen und Rückstöße. |
| Containerprüfung | Erkennt geschlossene Räume/Behälter. |
| Fraktionsprüfung | Prüft Sub-Pixel-Anteile und Aggregation. |
| Reaktionsprüfung | Prüft chemische/nukleare Umwandlungen. |

## Performance-Risiken

Eine vollständig manipulierbare Pixelwelt kann teuer werden.

Problematische Fälle:

- Explosionen
- viele bewegte Pixel/Zellen
- viele Kollisionen
- viele gleichzeitige Transformationen
- Gase/Flüssigkeiten mit Diffusion
- Wärmeausbreitung
- Feuer/Plasma
- chemische Kettenreaktionen

## Mögliche Optimierungsansätze

| Ansatz | Zweck |
|---|---|
| Chunking | Welt in größere Berechnungsbereiche teilen. |
| Spatial Partitioning | Kollisionen nur lokal prüfen. |
| LOD-Aggregation | entfernte/kleine Effekte gröber berechnen. |
| Aktivitätsmasken | nur aktive Bereiche aktualisieren. |
| Ereignisbasierte Updates | nur bei Änderung neu berechnen. |
| Grenzwerte/Cutoffs | irrelevante Kleinstwerte aggregieren. |
| Schlafende Partikel | ruhende Materialien nicht ständig simulieren. |
| Container-Regionen | Räume/Behälter als eigene Bilanzräume behandeln. |

## 2D-Levelstruktur

Eine mögliche Gameplay-Struktur:

- 2D-Welt mit links-nach-rechts-Fortschritt.
- Verschiedene Level führen Materialtypen, Spell-Makros und Simulationskonzepte schrittweise ein.
- Analyse- und Zaubermöglichkeiten wachsen mit Wissen/Bibliotheken.

## Zwei oder drei Ebenen?

Offen ist, ob die 2D-Welt nur eine Ebene besitzt oder mehrere Schichten.

Mögliche Modelle:

| Modell | Beschreibung |
|---|---|
| 2D-Ebene | klassische Seitenansicht oder Top-Down-Welt |
| 2.5D-Schichten | Vordergrund/Mitte/Hintergrund oder Materialschichten |
| 3 Ebenen | z. B. Oberfläche, Innenraum, Feld-/Energieebene |

## Offene Fragen

1. Ist die 2D-Welt eher Seitenansicht, Top-Down oder Hybrid?
2. Sind Weltzellen Pixel, Blöcke, Partikel oder hybride Zellen?
3. Wie werden Bewegungsvektoren stabil und performant berechnet?
4. Welche Stoffe werden lokal präzise simuliert und welche aggregiert?
5. Wie erkennt das System geschlossene Räume und Container?
6. Welche Ereignisse erzwingen hohe Simulationsauflösung?
7. Wie werden Explosionen begrenzt, ohne Erhaltungssätze zu brechen?
8. Welche Engine kann dieses Modell am besten tragen?
