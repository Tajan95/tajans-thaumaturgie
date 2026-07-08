# 2D Prototype

Dieser Ordner ist für spätere technische Experimente zur 2D-Simulation vorgesehen.

## Zielrichtung

Der erste Prototyp soll eine kleine 2D-Welt testen, in der Materie nicht nur Kulisse ist, sondern Zustandsträger für magische Operationen.

## Mögliche erste Simulationsziele

- pixel-/zellbasierte Welt mit flüssigen Bewegungsvektoren
- Zellen mit Position, Material, Phase, Temperatur und Bewegungszustand
- einfache Materialfraktionen, z. B. Luft als Mischung
- Zustandsänderungen wie Bewegen, Erwärmen, Abkühlen, Trennen, Binden
- Zielauswahl über Koordinaten, Radius, Objekt-ID oder Materialtyp
- Kostenberechnung für einfache Transformationen
- Abwärme als lokaler Effekt mit späterer Aggregation
- einfache Erhaltungsprüfer für Masse und Energie
- Fehlerfälle bei unklarer Zielauswahl, fehlendem Mana oder ungültigen Referenzen

## Frühe Materialtests

Geeignete Tests:

1. Wasser erhitzen/abkühlen und Phasenübergang prüfen.
2. Luft lokal in Bestandteile analysieren.
3. Gestein als homogenes Material anzeigen, aber intern Fraktionen speichern.
4. Kleine Gold-/Platinanteile als Sub-Pixel-Fraktionen erhalten.
5. CO₂ in offenem Raum vs. geschlossenem Raum unterschiedlich aggregieren.
6. Abwärme lokal präzise und regional/global grob bilanzieren.

## Performance-Fragen

Besonders kritisch:

- Explosionen
- viele bewegte Pixel/Zellen
- Kollisionen
- Wärmeausbreitung
- Gas-/Flüssigkeitsverteilung
- chemische Reaktionen
- Sub-Pixel-Fraktionen

## Status

Noch kein Prototyp implementiert.
