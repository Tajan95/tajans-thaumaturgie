# 05 — Energy, Costs and Limits

## Zweck

Dieses Dokument sammelt Modelle dafür, was Magie begrenzt.

Ein gutes Magie-System braucht Grenzen, sonst wird jeder Zauber beliebig.

---

## Grundentscheidung

Mana ist ein abstrakter Energie-/Arbeitsbegriff für magische Arbeit, vergleichbar mit Joule als Maßeinheit für Energie bzw. Arbeit.

Mana ist keine konkrete Substanz. Es beschreibt den bezahlbaren Aufwand, mit dem magische Operationen Zustände verändern können.

Nach DD-010 wird Mana zusätzlich als nutzbarer thaumischer Arbeitsfluss aus realen Energiepotentialen verstanden.

```text
Mana ≈ magische Arbeitswährung / Energieeinheit
Mana = nutzbarer thaumischer Arbeitsfluss aus realen Energiepotentialen
```

Siehe auch: `docs/23_mana_and_thaumic_field_model.md`.

## Thaumisches Feldpotential

Jede reale physikalische Energiequelle bzw. jedes reale Energiepotential kann ein gekoppeltes thaumisches Analog besitzen.

Dieses thaumische Potential ist keine zusätzliche Energiequelle, sondern eine magisch adressierbare Kopplungs- und Übertragungsebene für reale Energie.

```text
physikalisches Energiepotential
→ gekoppeltes thaumisches Potential
→ Zaubergeometrie koppelt daran
→ magische Arbeit
→ physikalische Quelle entlädt sich + Verluste
```

Eine Entladung des thaumischen Potentials entlädt daher immer auch das gekoppelte physikalische Analog.

Beispiele:

| Physikalische Quelle | Thaumisches Analog |
|---|---|
| chemische Energie | thaumisches Reaktionspotential |
| elektrische Spannung | thaumische Spannung |
| gespannte Feder | thaumisches mechanisches Potential |
| Temperaturgradient | thaumisches Wärmegefälle |
| bewegtes Wasser / Wind | thaumischer Arbeitsfluss |
| biologische Stoffwechselenergie | bio-thaumisches Potential |

## Quellen und Speicher

Mana kann aus unterschiedlichen Energiequellen stammen oder in unterschiedlichen Medien als metastabiles thaumisches Potential gespeichert sein.

| Quelle / Speicher | Beschreibung | Status |
|---|---|---|
| Biologische Energie | Lebewesen oder biologische Materie können durch magische Kopplung chemische Energie bereitstellen. | Festgelegt |
| Chemisch gebundene Energie | Fette, Öle, Kohlenhydrate oder andere chemische Speicher können als Energiequelle dienen. | Festgelegt durch DD-010 |
| Elektrische Energie | Batterien, Generatoren oder elektrische Potentiale können thaumisch angezapft werden, sofern eine gültige Kopplungsgeometrie existiert. | Festgelegt durch DD-010 |
| Mechanische Energie | Gespannte Federn, Rotation, Strömung oder fallende Massen können thaumische Arbeit speisen. | Festgelegt durch DD-010 |
| Thermische Energie | Wärme oder Temperaturgradienten können genutzt werden, erzeugen aber Abwärme- und Effizienzprobleme. | Hypothese |
| Externe Speicher | Kristalle, Artefakte oder andere Materialien speichern keine Mana-Substanz, sondern metastabile thaumische Potentialzustände. | Festgelegt durch DD-010 |
| Ritualstruktur | Rituale können Energie sammeln, speichern, kanalisieren oder stabilisieren. | Hypothese |

## Kein kognitives Mana

Der Begriff „kognitives Mana“ wird nicht als eigener Mana-Typ verwendet.

Kognitive Arbeit, Konzentration und Verständnis sind Kontroll- und Ausführungsflaschenhälse. Sie begrenzen also, **wie gut** ein Zauber konstruiert, gehalten oder kontrolliert werden kann, sind aber nicht die magische Energie selbst.

```text
Mana = Energie / Arbeit / thaumischer Arbeitsfluss
Kognition = Kontrolle / Syntaxverständnis / Ausführungsfähigkeit
```

## Erhaltungssätze

Vorläufig gelten folgende Grundsätze:

- Energie wird nicht erschaffen oder vernichtet.
- Masse wird nicht erschaffen oder vernichtet, außer ein expliziter Umwandlungsprozess ist definiert.
- Impuls muss berücksichtigt werden.
- Jeder Prozess erzeugt Verluste.
- Abwärme oder andere Nebenprodukte müssen berücksichtigt werden.
- Thaumische Entladung entlädt das gekoppelte physikalische Energiepotential.

Magie darf ungewöhnliche Transformationspfade ermöglichen, aber sie darf keine Energie oder Masse aus dem Nichts erzeugen.

## Vorläufige Kostenfaktoren

| Faktor | Beschreibung | Status |
|---|---|---|
| Physikalische Mindestarbeit | Mindestaufwand für die tatsächliche Zustandsänderung. | Festgelegt |
| Mana-Quelle | Woher die reale Energie stammt. | Festgelegt |
| Thaumisches Potential | Wie viel nutzbarer thaumischer Arbeitsfluss aus der Quelle verfügbar ist. | Festgelegt als Modellgröße |
| Kopplungseffizienz | Wie gut Quelle, Geometrie, Material und Ziel verbunden sind. | Hypothese |
| Komplexität | Aufwand für präzise oder mehrteilige Struktur. | Hypothese |
| Reichweite | Größere Distanz erhöht Kosten, Kontrollaufwand oder Fehlerwahrscheinlichkeit. | Hypothese |
| Dauer | Längere Wirkung erhöht Kosten oder Bindungsaufwand. | Hypothese |
| Zielwiderstand | Material, Masse oder Eigenstabilität des Ziels erschwert Veränderung. | Hypothese |
| Informationsmangel | Unklare Ziele oder Zustände erhöhen Risiko. | Hypothese |
| Konzentration / Kontrolle | Mentale Ausführungs- und Stabilisierungslast, aber keine Energiequelle. | Festgelegt |
| Medium | Kanal oder Träger der Wirkung. | Teilweise geklärt durch DD-010 |
| Verlustwärme | Unvermeidbare Nebenfolge ineffizienter Prozesse. | Festgelegt |
| Mana-Leckage | Verlust gespeicherten thaumischen Potentials über Zeit. | Hypothese |
| Entladerate | Wie schnell gespeichertes Potential sicher abgegeben werden kann. | Hypothese |
| Überlastung | Risiko bei zu hoher Spannung, zu schnellem Fluss oder schlechter Geometrie. | Hypothese |

## Vorläufige Kostenformel

```text
Gesamtkosten = physikalische Mindestarbeit
             × Komplexitätsfaktor
             × Distanzfaktor
             × Dauerfaktor
             × Zielwiderstand
             ÷ Kopplungseffizienz
             + Kontroll-/Stabilisierungskosten
             + Verlustkosten
```

**Status:** Arbeitsmodell

## Speicherformel / Kapazitätslogik

Ein Mana-Speicher ist kein Behälter für Mana-Teilchen, sondern ein Materialzustand, der thaumisches Potential halten kann.

```text
verfügbare Mana-Arbeit = min(
    gespeicherte thaumische Ladung,
    sichere Entladerate × Wirkzeit,
    durch Geometrie koppelbarer Anteil
) × Entladungseffizienz
```

Mögliche Speicherattribute:

| Attribut | Bedeutung |
|---|---|
| `mana_capacity` | Maximale speicherbare thaumische Arbeit / Potentialmenge. |
| `mana_charge` | Aktuell gespeicherte thaumische Ladung bzw. nutzbare Arbeit. |
| `thaumic_potential` | Aktuelle thaumische Spannung / Potentialhöhe. |
| `mana_conductivity` | Wie gut thaumischer Fluss durch das Material läuft. |
| `mana_leakage` | Wie schnell gespeichertes Potential verloren geht. |
| `mana_conversion_efficiency` | Wie gut reale Energie in nutzbaren thaumischen Arbeitsfluss gekoppelt wird. |
| `mana_discharge_rate` | Wie schnell gespeichertes Potential sicher abgegeben werden kann. |
| `mana_overload_threshold` | Grenze, ab der Material, Fokus oder Zauber instabil wird. |

## Beispiele

### Wasser zu Eis

Ein Zauber, der Wasser gefrieren lässt, muss mindestens die dafür nötige thermische Energie entfernen bzw. umlagern.

Der Zauber erzeugt also nicht einfach „Eis“, sondern bewirkt:

```text
Wasser + Wärmeentzug + Kristallisationsprozess + Wärmeabfuhr → Eis + abgeführte Wärme
```

Die entfernte Wärme verschwindet nicht. Sie muss in die Umgebung, ein Speichermedium oder einen anderen Prozess übertragen werden.

### Blei zu Gold

Blei zu Gold ist im System nicht prinzipiell verboten, aber es ist keine chemische, sondern eine nukleare Transformation.

Daraus folgt:

- extrem hoher Energiebedarf
- mögliche Strahlungs-/Nebenprodukte
- hohe Präzisionsanforderung
- sehr hohes Fehlerrisiko
- vermutlich ungeeignet für alltägliche Zauberei

### Illusion / Projektion

Eine Illusion verändert nicht zwingend Masse oder Materie. Sie kann als Lichtprojektion oder kontrollierte Wahrnehmungs-/Signalmanipulation modelliert werden.

Die Masse des scheinbar veränderten Objekts bleibt unverändert, sofern der Zauber keine echte Materieverteilung oder Transformation vornimmt.

### Zeitähnliche Effekte

Zeitumkehrung, Zeitverlangsamung oder Zeitbeschleunigung werden nicht als Bruch der Naturgesetze behandelt, sondern vorläufig als extrem präzise Manipulation von Zuständen, Vektoren, Prozessraten oder lokalen Dynamiken.

**Status:** Spekulative Hypothese. Muss später gesondert formalisiert werden.

### Körper als Mana-Quelle

Ein Zauberer ist nicht vollständig ohne Mana, solange sein Körper chemische Energie bereitstellen kann.

```text
Körperenergie
→ bio-thaumische Kopplung
→ Zauberarbeit
→ Erschöpfung + Unterzuckerung + Wärme + Stoffwechselstress
```

Große oder schnelle Entnahmen können zu Überhitzung, Bewusstlosigkeit, Gewebeschaden oder Tod führen.

### Geladener Kristall

Ein geladener Kristall enthält keine Mana-Partikel.

```text
Kristallstruktur + gespeicherte thaumische Spannung → nutzbarer Mana-Speicher
```

Der Kristall kann sich entladen, lecken, überlasten oder brechen, wenn seine Kapazität oder Entladerate überschritten wird.

## Mögliche Fehlerfälle

Fehler sollen bevorzugt emergent aus der Zauberstruktur entstehen.

| Fehlerfall | Ursache |
|---|---|
| Effekt verpufft | Zu wenig Mana oder falscher Zielbezug. |
| Effekt streut | Ungenaue Zielauswahl oder Form. |
| Effekt bricht ab | Mana-Quelle, Bibliothek, Fokusmedium oder Referenz wird während der Laufzeit unzugänglich. |
| Effekt kollabiert | Interne Widersprüche in Syntax oder Semantik. |
| Nebeneffekt | Unberücksichtigte Material-, Wärme-, Impuls- oder Zustandsrelationen. |
| Überhitzung | Verlustwärme wird nicht abgeführt. |
| Rückkopplung | Fehlerhafte Bindung zwischen Zauber, Fokusmedium, Speicher oder Zauberer. |
| Quellkollaps | Das gekoppelte physikalische Energiepotential wird schneller entladen als stabil möglich. |
| Speicherbruch | Thaumische Spannung überschreitet Kapazität oder Strukturgrenze des Speichers. |
| Bio-Schaden | Körperenergie wird zu schnell oder zu tief entzogen. |

## Offene Grundfragen

1. Gibt es eine direkte Mana-Joule-Umrechnung?
2. Wie wird `thaumic_potential` quantitativ aus physikalischen Energiepotentialen berechnet?
3. Wie exakt werden Enthalpie, Impuls und Abwärme im 2D-Prototyp simuliert?
4. Gibt es neben physikalischer Abwärme auch magische Entropie oder „Mana-Abwärme“?
5. Wann brauchen wir abstrakte Misslingen-Modifier, statt Fehler rein emergent entstehen zu lassen?
6. Welche Materialien besitzen welche Mana-Attribute?
7. Wie werden Kopplungseffizienz, Leckage, Entladerate und Überlastung in der Engine berechnet?
