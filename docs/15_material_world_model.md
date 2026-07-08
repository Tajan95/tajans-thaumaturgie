# 15 — Material World Model

Dieses Dokument beschreibt das frühe Modell der materiellen Spielwelt.

**Status:** Arbeitsmodell / offene Simulationsfragen

---

## Grundidee

Die Welt soll nicht aus abstrakten, unzerstörbaren Objekten bestehen, sondern aus manipulierbarer Materie mit Eigenschaften, Zusammensetzungen und Zuständen.

Magie wirkt dadurch nicht auf hardcodierte Objekte, sondern auf beschreibbare Zustände und Materialien.

```text
Element → Substanz/Stoff → Material → Objekt → Weltzustand
```

## Grundentscheidung: Materiegebundene Standardmagie

Standardmagie koppelt direkt an vorhandene Materie und deren Zustände.

Das bedeutet:

- Materie kann bewegt, erwärmt, abgekühlt, getrennt, gebunden, verformt oder transformiert werden.
- Kontaktlose Kraftvektoren auf Materie sind erlaubt.
- Direkte substratlose Feld-/Wellenmanipulation ist keine Standardmagie.
- Direkte EM-/Photonen-/Feldmagie bleibt als spätere High-Level-Interventionsklasse offen.

Siehe auch: `docs/18_intervention_classes.md`.

## Modellschichten

| Ebene | Bedeutung | Beispiel |
|---|---|---|
| Element | chemisches Grundelement oder funktionaler Elementtyp | Sauerstoff, Eisen, Silizium |
| Substanz / Stoff | molekulare oder chemische Verbindung | Wasser, Quarz, NaCl |
| Material | spielpraktische Materialklasse mit Eigenschaften | Holz, Stein, Fleisch, Öl |
| Objekt | zusammengesetzte Struktur aus Materialien | Baum, Tür, Felsblock |
| Weltzelle / Pixel | kleinste simulierte räumliche Einheit | Materialfraktion in 2D-Welt |

## Elementkatalog

Das System benötigt voraussichtlich keinen vollständigen Periodensystem-Katalog, sondern einen funktional ausreichenden Ausschnitt.

Vorläufig genannte Elemente:

```text
H, He?, Ar, C, N, P, O, S, Cl, Na, Ca, Mg?, Fe, Cu, Ag, Au, Pt,
Pb, Hg?, U, Al?, Ti?, Li?, Si, F?, K?, Sn?, Zn?, W?
```

### Offene Auswahlkriterien

Ein Element sollte aufgenommen werden, wenn es mindestens eine klare Funktion erfüllt:

- häufige natürliche Substanzen erklären
- wichtige Materialeigenschaften erzeugen
- interessante Zauberinteraktionen ermöglichen
- Reaktivität, Leitfähigkeit, Magnetismus oder Dichte erklären
- für Gameplay oder Rätsel relevant sein

## Material- und Stoffkatalog

Neben Elementen braucht das System pragmatisch gewählte Stoffe und Materialien.

Beispiele:

- Wasser
- Luft
- Sand
- Boden
- Gestein
- Holz
- Rinde
- photosynthetisches Gewebe
- Meristem
- Fleisch
- Blut
- Öl/Fett
- Magma
- Glas
- Metalllegierungen

## Materialattribute

Materialien und Stoffe können Attribute besitzen wie:

| Attribut | Bedeutung |
|---|---|
| Dichte | Masse pro Volumen |
| Härte | Widerstand gegen Eindringen/Verformung |
| Leitfähigkeit | elektrische oder thermische Leitfähigkeit |
| Entflammbarkeit | Neigung zur Verbrennung |
| Reaktivität | chemische Aktivität |
| Säure-/Laugenempfindlichkeit | Reaktion mit pH-Extremen |
| Magnetismus | Reaktion auf Magnetfelder |
| Reflektivität | Verhalten gegenüber Licht |
| Elastizität | Rückstellverhalten nach Verformung |
| Reibung | Oberflächenwiderstand |
| Viskosität | Fließwiderstand bei Flüssigkeiten |
| Gefrier-/Siedepunkt | Phasenübergänge |
| Bruchmodus | Splittern, Reißen, Krümeln, Verformen, Explodieren |
| chemische Energie | gespeicherte Reaktionsenergie |

## Phasenmodell

Vorläufige Phasen:

```text
fest
flüssig
gasförmig
Plasma
```

Feuer ist kein Grundelement.

Feuer wird stattdessen als Kombination aus Prozess und Zustand verstanden:

```text
Feuer = Wärme + chemische Reaktion + Lichtemission + ggf. Plasma/ionisierte Gase
```

Magisches Feuer wäre entsprechend kein Element, sondern ein zusammengesetzter Effekt aus Energieeintrag, Materialreaktion und ggf. Plasma.

## Kompositmaterialien

Kompositmaterialien können als homogene Masse angezeigt werden, solange keine Analyse oder Trennung stattfindet.

Intern behalten sie eine Zusammensetzung.

Beispiel:

```text
Gestein = Quarz/Silikate + metallische/ionische Spurenelemente + Salze
```

Komplexes Beispiel:

```text
Baum = Holz + Rinde + photosynthetisches Gewebe + Meristem + Wasseranteile
```

## Materialanalyse

Materialanalyse kann progressive Detailtiefe haben.

Frühe Analyse:

```text
Luft: 78% Stickstoff, 21% Sauerstoff, 2% unbekannter Rest
```

Spätere Analyse:

```text
Luft: 78% Stickstoff, 20.95% Sauerstoff, 0.93% Argon, Spuren CO₂, Wasserdampf variabel
```

## Materialanalyse als Fähigkeit oder Zauber

Offen ist, ob Materialanalyse eine inhärente Spielerfähigkeit, ein Zauber, ein Artefakt oder ein UI-Hilfsmittel ist.

Mögliche Modelle:

| Modell | Bedeutung |
|---|---|
| Grundfähigkeit | Spieler kann einfache Materialien immer grob erkennen. |
| Analysezauber | Detailtiefe hängt von Zauber, Mana und Wissen ab. |
| Artefaktfunktion | Analyse benötigt Werkzeug oder Fokusmedium. |
| Wissensprogression | bekannte Elemente/Materialien werden nach und nach aufgedeckt. |
| Hybrid | grobe Analyse kostenlos, tiefe Analyse als Zauber/Tool. |

## Beispiele für emergente Zaubermotive

### Opfer als biologische Manaquelle

Wenn biologische oder chemisch gebundene Energie als Manaquelle dienen kann, ergeben sich Tier- oder Menschenopfer als mögliche Ritualform, ohne als Spezialregel hardcodiert zu werden.

```text
biologische Materie → magische Energiequelle → Ritualarbeit + Nebenprodukte
```

Das Motiv ist morbide, aber systemisch konsistent.

### Blei zu Gold

Blei zu Gold ist keine chemische, sondern nukleare Transformation. Es ist dadurch prinzipiell denkbar, aber extrem energieintensiv und riskant.

### Schwebendes Licht

Nach DD-009 ist die Standardvariante eines schwebenden Lichtes materiegebunden.

Mögliche Standard-Modellierungen:

1. Luftplasma durch Energieeintrag.
2. erhitztes materielles Medium.
3. ionisierte oder angeregte Partikel als Lichtquelle.

Direkte elektromagnetische Emission ohne materielles Substrat ist nicht Standardmagie. Sie bleibt als spätere High-Level-Interventionsklasse möglich.

### Schweben / Telekinese

Ein Schwebezauber wirkt direkt auf ein materielles Ziel, indem er Kraftvektoren bzw. Impulsänderungen erzeugt.

```text
materielles Ziel + Kraftvektor + Stabilisierung + Energieaufwand → Schweben
```

## Offene Fragen

1. Welche Elemente sind für den ersten Prototyp nötig?
2. Welche Materialattribute sind zwingend, welche optional?
3. Wie detailliert müssen natürliche Objekte intern modelliert werden?
4. Ist Materialanalyse Grundfähigkeit, Zauber, Artefakt oder UI?
5. Wie werden Säuren, Laugen, Strom und Magnetfelder repräsentiert?
6. Wie wird Plasma im ersten 2D-Prototyp abstrahiert?
7. Wann, wenn überhaupt, wird High-Level-Feld-/Wellenmagie eingeführt?
