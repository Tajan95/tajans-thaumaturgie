# 03 — Spell Syntax

## Zweck

Dieses Dokument beschreibt, wie ein Zauber formal aufgebaut sein könnte.

Die zentrale Frage lautet:

> Aus welchen syntaktischen Bestandteilen besteht ein Zauber?

## Vorläufiges Schema

```text
Zauber := Ziel + Wirkung + Struktur + Modifier + Kosten + Bedingung
```

## Komponenten

| Komponente | Funktion | Beispiel |
|---|---|---|
| Ziel | Bestimmt, worauf der Zauber wirkt. | Objekt, Fläche, Richtung, Lebewesen |
| Wirkung | Bestimmt, was verändert wird. | erhitzen, bewegen, binden, trennen |
| Struktur | Bestimmt die Form der Wirkung. | Linie, Kreis, Kegel, Punkt, Feld |
| Modifier | Verändert Parameter der Wirkung. | verstärken, umkehren, verzögern |
| Kosten | Beschreibt Aufwand und Begrenzung. | Energie, Konzentration, Material |
| Bedingung | Legt Auslöse- oder Gültigkeitslogik fest. | bei Kontakt, solange sichtbar, nach Zeit |

## Beispiel als abstrakte Form

```text
Ziel: Wasserfläche
Wirkung: Temperatur senken
Struktur: Kreisfläche
Modifier: Dauer 10 Sekunden
Kosten: proportional zu Fläche und Temperaturdifferenz
Ergebnis: lokale Vereisung
```

## Offene Fragen

1. Gibt es eine feste Reihenfolge der Zauberkomponenten?
2. Werden Zauber eher als lineare Sequenz, Graph oder verschachtelte Struktur modelliert?
3. Können mehrere Wirkungen parallel in einem Zauber laufen?
4. Wie werden Syntaxfehler oder semantische Widersprüche behandelt?
