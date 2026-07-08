# 18 — Intervention Classes

Dieses Dokument definiert frühe Interventionsklassen: also worauf Magie direkt zugreifen darf.

**Status:** Grundentscheidung für Standardmagie festgelegt; High-Level-Klassen offen.

---

## Begriff

Eine Interventionsklasse beschreibt, welche Art von physikalischem Ziel ein Zauber direkt manipuliert.

Nicht entscheidend ist nur, welcher Effekt am Ende sichtbar wird, sondern worauf der Zauber unmittelbar zugreift.

```text
Interventionsklasse = direkter Zugriffstyp eines Zaubers
```

## Grundentscheidung

Standardmagie ist materiegebunden.

Das bedeutet:

```text
Magie koppelt standardmäßig an vorhandene Materie und deren Zustände.
```

Magie erzeugt in der Standardauslegung keine substratlosen Felder, Photonen oder elektromagnetischen Wellen direkt aus dem Nichts.

## Klasse 1 — Materiegebundene Manipulation

Diese Klasse ist die Standardklasse des Systems.

Direkt manipulierbar sind z. B.:

- Position
- Geschwindigkeit
- Kraftvektoren / Impulsänderung
- Temperatur
- Phase
- Druck
- chemische Bindungen
- Ladungsverteilung in Materie
- Zusammensetzung
- Materialtrennung
- Form / Verformung

## Kontaktlose Kraftvektoren

Kontaktlose Kraftvektoren auf Materie sind erlaubt.

Beispiele:

- Stein heben
- Wasser bewegen
- Luft beschleunigen
- Metall verbiegen
- Objekt schweben lassen

Bedingungen:

- Es gibt ein materielles Ziel.
- Zielbezug und Reichweite sind definiert.
- Energieaufwand wird bezahlt.
- Impulsbilanz und Nebenwirkungen werden berücksichtigt.
- Fehlerbedingungen sind möglich.

## Klasse 2 — Feld-/Wellenmanipulation

Diese Klasse ist vorläufig keine Standardmagie, bleibt aber als spätere High-Level-Magie möglich.

Mögliche direkte Ziele:

- Photonen
- elektromagnetische Wellen
- elektrische Felder
- Magnetfelder
- Licht im Vakuum
- substratlose Signal- oder Feldmuster

## Warum Klasse 2 nicht Standard ist

Direkte Feld-/Wellenmanipulation öffnet sehr mächtige Effektbereiche:

- Laser
- präzise Lichtformung
- Funk/Kommunikation
- EMP-artige Effekte
- Magnetfeldfallen
- Sensorik im großen Radius
- Illusionen ohne Projektionsmedium

Diese Effekte sind nicht grundsätzlich verboten, würden aber das System deutlich erweitern und sollten daher später separat formalisiert werden.

## Beispiele

### Schwebendes Licht — Standardvariante

Ein einfacher Lichtzauber braucht eine materielle Basis.

Mögliche Konstruktion:

```text
Luft + Energieeintrag → ionisierte Luft / Plasma → sichtbares Leuchten
```

oder:

```text
Partikel/Medium erhitzen → Lichtemission
```

### Schwebendes Licht — High-Level-Variante

Eine spätere High-Level-Variante könnte direkte EM-Wellen erzeugen:

```text
Mana-Arbeit → elektromagnetische Wellen im sichtbaren Spektrum
```

Diese Variante wäre teurer, komplexer und würde höhere Präzision sowie spezielle Syntax/Bibliotheken erfordern.

### Schweben / Telekinese

Ein Schwebezauber ist keine Felderschaffung, sondern Kraft-/Impulsmanipulation eines materiellen Zieles:

```text
materielles Ziel + Kraftvektor + Stabilisierung + Energieaufwand → Schweben
```

## Konsequenz für Simulation

Der erste 2D-Prototyp sollte Klasse 1 priorisieren:

- Materie bewegen
- Materie erwärmen/abkühlen
- Phasen ändern
- Materialien trennen
- Druck/Luftbewegung erzeugen
- einfache Ladungs-/Strom-/Magnetismus-Effekte über Materie testen

Klasse 2 wird nicht für den ersten Prototyp benötigt.

## Offene Fragen

1. Welche Bedingungen erlauben später direkte Feld-/Wellenmagie?
2. Welche zusätzlichen Kostenfaktoren entstehen für Klasse 2?
3. Welche Bibliotheken/Syntax braucht direkte EM-Manipulation?
4. Gibt es Zwischenklassen, z. B. Feldmanipulation nur in/um Materie?
5. Wie wird verhindert, dass Klasse 2 Standardmagie trivial überflüssig macht?
