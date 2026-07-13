# 15 — Material World Model

**Stand:** 2026-07-14, 01:44 Europe/Berlin  
**Status:** Arbeitsmodell / offene Simulationsfragen

Dieses Dokument beschreibt das frühe Modell der materiellen Spielwelt.

Ergänzende Dokumente:

- `world_resolution_and_quantity_model.md`
- `world_cell_and_chunk_model.md`
- `../spell_system/target_and_effect_node_model.md`

---

## Grundidee

Die Welt soll nicht aus abstrakten, unzerstörbaren Objekten bestehen, sondern aus manipulierbarer Materie mit Eigenschaften, Zusammensetzungen und Zuständen.

Magie wirkt dadurch nicht auf hardcodierte Objekte, sondern auf beschreibbare Zustände und Materialien.

```text
Element → Substanz/Stoff → Material → Objekt → Weltzustand
```

---

## Grundentscheidung: Materiegebundene Standardmagie

Standardmagie koppelt direkt an vorhandene Materie und deren Zustände.

Das bedeutet:

- Materie kann bewegt, erwärmt, abgekühlt, getrennt, gebunden, verformt oder transformiert werden.
- Kontaktlose Kraftvektoren auf Materie sind erlaubt.
- Direkte substratlose Feld-/Wellenmanipulation ist keine Standardmagie.
- Direkte EM-/Photonen-/Feldmagie bleibt als spätere High-Level-Interventionsklasse offen.

---

## Modellschichten

| Ebene | Bedeutung | Beispiel |
|---|---|---|
| Element | chemisches Grundelement oder funktionaler Elementtyp | Sauerstoff, Eisen, Silizium |
| Substanz / Stoff | molekulare oder chemische Verbindung | Wasser, Quarz, NaCl |
| Material | spielpraktische Materialklasse mit Eigenschaften | Holz, Stein, Fleisch, Öl |
| Objekt | zusammengesetzte Struktur aus Materialien | Baum, Tür, Felsblock |
| WorldCell | kleinste simulierte räumliche Einheit | lokaler Weltzustand |
| Stofffraktion | Sub-Zell-Masse eines Bestandteils | CO₂-Anteil in Luft |

Eine WorldCell ist keine Mindestmasse und keine Mindeststoffmenge.

---

## Elementkatalog

Das System benötigt voraussichtlich keinen vollständigen Periodensystem-Katalog, sondern einen funktional ausreichenden Ausschnitt.

Vorläufig genannte Elemente:

```text
H, He?, Ar, C, N, P, O, S, Cl, Na, Ca, Mg?, Fe, Cu, Ag, Au, Pt,
Pb, Hg?, U, Al?, Ti?, Li?, Si, F?, K?, Sn?, Zn?, W?
```

### Auswahlkriterien

Ein Element sollte aufgenommen werden, wenn es mindestens eine klare Funktion erfüllt:

- häufige natürliche Substanzen erklären
- wichtige Materialeigenschaften erzeugen
- interessante Zauberinteraktionen ermöglichen
- Reaktivität, Leitfähigkeit, Magnetismus oder Dichte erklären
- für Gameplay oder Rätsel relevant sein

---

## Material- und Stoffkatalog

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

---

## Materialattribute

| Attribut | Bedeutung |
|---|---|
| Dichte | Masse pro effektivem Volumen |
| Wärmekapazität | Energiebedarf pro Temperaturänderung |
| Wärmeleitfähigkeit | Wärmeübertragung im Material |
| elektrische Leitfähigkeit | Ladungs- und Stromtransport |
| Härte | Widerstand gegen Eindringen oder Verformung |
| Elastizität | Rückstellverhalten |
| Reibung | Oberflächenwiderstand |
| Viskosität | Fließwiderstand |
| Entflammbarkeit | Neigung zur Verbrennung |
| Reaktivität | chemische Aktivität |
| Säure-/Laugenempfindlichkeit | Reaktion mit pH-Extremen |
| Magnetismus | Reaktion auf magnetische Felder |
| Reflektivität | Verhalten gegenüber Licht |
| Gefrier-/Siedepunkt | Phasenübergänge |
| Bruchmodus | Splittern, Reißen, Krümeln, Verformen |
| chemische Energie | gespeicherte Reaktionsenergie |
| nukleare Zusammensetzung | Isotope und Kernzustände bei High-Level-Transformation |

---

## Phasenmodell

Vorläufige Phasen:

```text
fest
flüssig
gasförmig
Plasma
```

Feuer ist kein Grundelement.

```text
Feuer = Wärme + chemische Reaktion + Lichtemission + ggf. Plasma
```

Magisches Feuer ist entsprechend ein zusammengesetzter Effekt aus Materialauswahl, Energieeintrag, Reaktion, Stofftransport und gegebenenfalls Ionisierung.

---

## Kompositmaterialien und Sub-Zell-Fraktionen

Kompositmaterialien können als homogene oder dominante Materialklasse angezeigt werden, solange keine Analyse oder Trennung stattfindet.

Intern behalten sie ihre Zusammensetzung.

```text
Gestein = Silikate + metallische Anteile + Salze + Spurenelemente
```

```text
Luft = Stickstoff + Sauerstoff + Argon + CO₂ + Wasserdampf
```

Kleine Stoffmengen werden nicht auf ein vollständiges Pixelvolumen aufgerundet. Sie bleiben als Sub-Zell-Massen in einer `Composition` erhalten.

Ein Trennzauber kann mehrere solche Fraktionen akkumulieren, bis eine sichtbare oder technisch relevante Stoffmenge entsteht.

---

## Gemischtypen

| Typ | Beispiel | Bedeutung |
|---|---|---|
| homogen | Luft, Lösung, Legierung | Bestandteile werden als gemeinsame Phase behandelt |
| heterogenes Partikelgemisch | Sand mit Goldstaub | diskrete, aber subzellulär aggregierte Partikel |
| Kompositstruktur | Holz mit Stahlbeschlägen | räumlich/strukturell getrennte Komponenten |
| porös | Erde, Schaum | Feststoff und Gas/Flüssigkeit teilen Raumanteile |
| biologisch organisiert | Gewebe, Organ | Material plus funktionale Struktur und Zustände |

Die Art des Gemischs beeinflusst, welche Trenn-, Analyse- und Transformationsoperationen zulässig oder teuer sind.

---

## Hierarchische Objekte

Stabile makroskopische Gegenstände werden möglichst als aggregierte Objekte simuliert.

```text
RigidObject {
    geometry
    mass
    center_of_mass
    position_subcell
    orientation
    linear_velocity
    angular_velocity
    material_composition
}
```

Gesamtmasse:

```text
Gesamtmasse = Σ (Dichte_i × Volumen_i)
```

Erst lokale stoffliche oder strukturelle Eingriffe verlangen eine feinere Zell-, Komponenten- oder Fragmentauflösung.

---

## Physikalische Effect-Domänen

Die materielle Welt muss mindestens folgende Standardoperationen unterstützen:

| Domäne | Veränderte Zustände | Beispiele |
|---|---|---|
| mechanisch-kinematisch | Position, Impuls, Geschwindigkeit, Rotation | bewegen, beschleunigen, drehen |
| mechanisch-strukturell | Spannung, Dehnung, Form, Bruch | biegen, komprimieren, spalten |
| thermisch | innere Energie und Temperatur | erhitzen, abkühlen |
| elektrisch in Materie | Ladung, Verteilung, Strom | laden, entladen, Strom treiben |
| kompositionell / Transport | Stoffverteilung | filtern, trennen, konzentrieren |
| chemisch | Molekül- und Bindungsstruktur | Reaktionen ausführen |
| phasenbezogen | Aggregatzustand | schmelzen, verdampfen, ionisieren |
| nuklear | Kern-/Isotopenzusammensetzung | Transmutation |

Diese Domänen sind keine fertigen Zauber. Sie sind Familien atomarer Zustandsoperationen.

---

## Information ist keine materielle Effect-Domäne

Suchen, Erkennen, Klassifizieren und Filtern werden als Query-/Analysis-Operationen modelliert.

Sie können Informationen oder TargetSets erzeugen, verändern aber nicht zwangsläufig Materie.

Ihre Kosten entstehen unter anderem durch:

- Größe des Suchraums
- Auflösung
- Bibliothekswissen
- Aktualisierungsfrequenz
- Unsicherheit
- Zielkomplexität

---

## Biologische und kognitive Effekte

Biologische Organismen bestehen aus Materie, chemischen Zuständen, elektrischen Signalen und komplexer räumlicher Organisation.

Daher wird vorläufig keine unabhängige elementare Domäne `Kognition` eingeführt.

Kognitive Makros müssen auf zugrunde liegende Operationen zurückführbar sein.

### Tierkommunikation

```text
sensorische Signale erfassen
+ Muster analysieren
+ Bedeutung über Wissen/Bibliothek abbilden
+ kompatible Antwortsignale erzeugen
```

### Beeinflussung eines Gehirns

```text
biologische Zielregion identifizieren
+ elektrische/chemische Zustände manipulieren
+ Rückkopplung beobachten
+ Sicherheits- und Fehlerlogik
```

Direkte mentale Wirkung ohne materielles neuronales Substrat ist keine Standardmagie.

Solche Eingriffe bleiben prinzipiell möglich, sind aber extrem informationsintensiv, individuell, fehleranfällig und physisch gefährlich.

---

## Materialanalyse

Materialanalyse kann progressive Detailtiefe haben.

Frühe Analyse:

```text
Luft: überwiegend Stickstoff und Sauerstoff, Rest unbekannt
```

Spätere Analyse:

```text
Luft: genaue Stoffmassen, Spurengase, Temperatur, Druck, Feuchtigkeit
```

Mögliche Modelle:

| Modell | Bedeutung |
|---|---|
| Grundfähigkeit | grobe Materialien immer erkennbar |
| Analysezauber | Detailtiefe kostet Energie und Kontrolle |
| Artefaktfunktion | Analyse benötigt Werkzeug |
| Wissensprogression | bekannte Stoffe werden präziser erkannt |
| Hybrid | grobe Analyse frei, tiefe Analyse als Query-/Analysegraph |

---

## Beispiele emergenter Zaubermotive

### Opfer als biologische Energiequelle

```text
biologische Energiequelle
→ thaumischer Arbeitsfluss
→ Ritualarbeit
→ Erschöpfung, Wärme und Gewebeschaden
```

### Blei zu Gold

Blei-zu-Gold ist eine nukleare, keine chemische Transformation. Sie ist prinzipiell beschreibbar, aber extrem energieintensiv und mit Strahlung, Nebenprodukten und Präzisionsanforderungen verbunden.

### Schwebendes Licht

Standardvarianten benötigen ein materielles Medium:

1. ionisierte Luft oder Plasma
2. erhitzte Partikel
3. angeregte Materie als Lichtquelle

Direkte substratlose Photonenerzeugung bleibt High-Level-Feld-/Wellenmagie.

### Schweben / Telekinese

```text
materielles Ziel
+ ApplyForce / Impulsänderung
+ Referenzrahmen
+ Stabilisierung
+ Energie- und Gegenimpulsbilanz
→ Schweben
```

---

## Offene Fragen

1. Welche Elemente und Stoffe sind für den ersten Prototyp nötig?
2. Welche Materialattribute sind zwingend, welche optional?
3. Wie detailliert müssen natürliche und biologische Objekte intern modelliert werden?
4. Wie werden Säuren, Laugen, Plasma und Magnetfelder abstrahiert?
5. Welche atomaren chemischen und nuklearen Operationen werden tatsächlich angeboten?
6. Welche Wissens- und Analysemodelle erlauben biologische Zielauswahl?
7. Ab welcher Komplexität werden biologische oder kognitive Makros praktisch nicht mehr beherrschbar?
8. Wann wird High-Level-Feld-/Wellenmagie eingeführt?
