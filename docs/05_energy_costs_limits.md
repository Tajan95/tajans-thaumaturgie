# 05 — Energy, Costs and Limits

## Zweck

Dieses Dokument sammelt Modelle dafür, was Magie begrenzt.

Ein gutes Magie-System braucht Grenzen, sonst wird jeder Zauber beliebig.

---

## Grundentscheidung

Mana ist vorläufig ein abstrakter Energie-/Arbeitsbegriff für magische Arbeit, vergleichbar mit Joule als Maßeinheit für Energie bzw. Arbeit.

Mana ist keine konkrete Substanz. Es beschreibt den bezahlbaren Aufwand, mit dem magische Operationen Zustände verändern können.

```text
Mana ≈ magische Arbeitswährung / Energieeinheit
```

## Quellen und Speicher

Mana kann aus unterschiedlichen Quellen stammen oder in unterschiedlichen Medien gespeichert sein.

| Quelle / Speicher | Beschreibung | Status |
|---|---|---|
| Biologische Energie | Lebewesen oder biologische Materie können durch magische „Verbrennung“ Energie bereitstellen. | Festgelegt |
| Chemisch gebundene Energie | Fette, Öle, Kohlenhydrate oder andere chemische Speicher können als Energiequelle dienen. | Hypothese |
| Externe Speicher | Kristalle, Artefakte oder andere Materialien können Mana speichern. | Hypothese |
| Umweltenergie | Wärme, Bewegung, Licht oder andere vorhandene Energieformen könnten umgewandelt werden. | Offene Frage |
| Ritualstruktur | Rituale können Energie sammeln, speichern, kanalisieren oder stabilisieren. | Hypothese |

## Kein kognitives Mana

Der Begriff „kognitives Mana“ wird nicht als eigener Mana-Typ verwendet.

Kognitive Arbeit, Konzentration und Verständnis sind Kontroll- und Ausführungsflaschenhälse. Sie begrenzen also, **wie gut** ein Zauber konstruiert, gehalten oder kontrolliert werden kann, sind aber nicht die magische Energie selbst.

```text
Mana = Energie / Arbeit
Kognition = Kontrolle / Syntaxverständnis / Ausführungsfähigkeit
```

## Erhaltungssätze

Vorläufig gelten folgende Grundsätze:

- Energie wird nicht erschaffen oder vernichtet.
- Masse wird nicht erschaffen oder vernichtet, außer ein expliziter Umwandlungsprozess ist definiert.
- Impuls muss berücksichtigt werden.
- Jeder Prozess erzeugt Verluste.
- Abwärme oder andere Nebenprodukte müssen berücksichtigt werden.

Magie darf ungewöhnliche Transformationspfade ermöglichen, aber sie darf keine Energie oder Masse aus dem Nichts erzeugen.

## Vorläufige Kostenfaktoren

| Faktor | Beschreibung | Status |
|---|---|---|
| Physikalische Mindestarbeit | Mindestaufwand für die tatsächliche Zustandsänderung. | Festgelegt |
| Mana-Quelle | Woher die Energie stammt. | Festgelegt |
| Komplexität | Aufwand für präzise oder mehrteilige Struktur. | Hypothese |
| Reichweite | Größere Distanz erhöht Kosten, Kontrollaufwand oder Fehlerwahrscheinlichkeit. | Hypothese |
| Dauer | Längere Wirkung erhöht Kosten oder Bindungsaufwand. | Hypothese |
| Zielwiderstand | Material, Masse oder Eigenstabilität des Ziels erschwert Veränderung. | Hypothese |
| Informationsmangel | Unklare Ziele oder Zustände erhöhen Risiko. | Hypothese |
| Konzentration / Kontrolle | Mentale Ausführungs- und Stabilisierungslast, aber keine Energiequelle. | Festgelegt |
| Medium | Kanal oder Träger der Wirkung. | Offene Frage |
| Verlustwärme | Unvermeidbare Nebenfolge ineffizienter Prozesse. | Festgelegt |

## Vorläufige Kostenformel

```text
Gesamtkosten = physikalische Mindestarbeit
             × Komplexitätsfaktor
             × Distanzfaktor
             × Dauerfaktor
             × Zielwiderstand
             + Kontroll-/Stabilisierungskosten
             + Verlustkosten
```

**Status:** Arbeitsmodell

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

## Offene Grundfragen

1. Gibt es eine direkte Mana-Joule-Umrechnung?
2. Welche Energieformen können in Mana-Arbeit umgewandelt werden?
3. Wie exakt werden Enthalpie, Impuls und Abwärme im 2D-Prototyp simuliert?
4. Gibt es neben physikalischer Abwärme auch magische Entropie oder „Mana-Abwärme“?
5. Wann brauchen wir abstrakte Misslingen-Modifier, statt Fehler rein emergent entstehen zu lassen?
