# 03 — Spell Syntax

## Zweck

Dieses Dokument beschreibt, wie ein Zauber formal aufgebaut sein könnte.

Die zentrale Frage lautet:

> Aus welchen syntaktischen Bestandteilen besteht ein Zauber?

## Vorläufiges Schema

```text
Zauber := Ziel
        + Wirkung
        + Struktur
        + Modifier
        + Kosten/Energiequelle
        + Bedingung
        + Kontrollanforderung
        + Fehlerlogik
        + physische visuelle Repräsentation
```

## Komponenten

| Komponente | Funktion | Beispiel |
|---|---|---|
| Ziel | Bestimmt, worauf der Zauber wirkt. | Objekt, Fläche, Richtung, Lebewesen |
| Wirkung | Bestimmt, was verändert wird. | erhitzen, bewegen, binden, trennen |
| Struktur | Bestimmt die Form der Wirkung. | Linie, Kreis, Kegel, Punkt, Feld |
| Modifier | Verändert Parameter der Wirkung. | verstärken, umkehren, verzögern |
| Kosten/Energiequelle | Beschreibt Mana-Aufwand und Quelle. | Körperenergie, Kristall, Artefakt, Umweltwärme |
| Bedingung | Legt Auslöse- oder Gültigkeitslogik fest. | bei Kontakt, solange sichtbar, nach Zeit |
| Kontrollanforderung | Beschreibt mentale oder motorische Ausführungslast. | Konzentration, Timing, Präzision |
| Fehlerlogik | Beschreibt mögliche Abbrüche oder Fehlwirkungen. | Energiemangel, ungültiges Ziel, Syntaxfehler |
| Visuelle Repräsentation | Macht den Zauber in-world ausführbar. | Schriftrolle, Gravur, Tattoo, Ritualkreis |

## Beispiel als abstrakte Form

```text
Ziel: Wasserfläche
Wirkung: Temperatur senken
Struktur: Kreisfläche
Modifier: Dauer 10 Sekunden
Kosten: proportional zu Fläche und Temperaturdifferenz
Energiequelle: Kristall oder Körper
Nebenprodukt: abgeführte Wärme
Repräsentation: gezeichneter Kreiszauber auf Trägermedium
Ergebnis: lokale Vereisung, wenn Wärmeabfuhr und Kosten gedeckt sind
```

## Syntaxfehler und Laufzeitfehler

Ein Zauber verhält sich analog zu einem Programm.

| Fehlertyp | Beschreibung | Beispiel |
|---|---|---|
| Syntaxfehler | Die Struktur ist formal ungültig. | fehlender Zielblock, unverbundener Modifier |
| Semantikfehler | Die Struktur ist formal korrekt, aber bedeutungslos oder widersprüchlich. | `erhitze` + `senke Temperatur` ohne Priorität |
| Ressourcenfehler | Der Zauber ist gültig, aber nicht bezahlbar. | zu wenig Mana im Speicher |
| Referenzfehler | Eine benötigte Quelle, Bibliothek, Bindung oder Repräsentation fehlt. | Runenfragment zerstört, Kristall entfernt |
| Laufzeitfehler | Während der Ausführung ändern sich Bedingungen. | Ziel verlässt Bereich, Fokus bricht |

Fehler sollen bevorzugt emergent aus der konkreten Zauberstruktur entstehen. Abstrakte Misslingen-Modifier bleiben vorläufig offen.

## Offene Fragen

1. Gibt es eine feste Reihenfolge der Zauberkomponenten?
2. Werden Zauber eher als lineare Sequenz, Graph, Syntaxbaum oder Komponentenobjekt modelliert?
3. Können mehrere Wirkungen parallel in einem Zauber laufen?
4. Wie werden visuelle Syntaxfehler erkannt und diagnostiziert?
5. Wann ist eine physische Repräsentation beschädigt, aber noch teilweise ausführbar?
