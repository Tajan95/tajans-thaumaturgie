# Clustered Notes — 2026-07-08

Dieses Dokument verarbeitet die Rohnotizen vom 08.07.2026 und gleicht sie gegen den bisherigen Projektstand ab.

---

## 1. Meta- und Projektarbeitsfragen

### Inhalte

- Game-Engine-Wahl
- Feedbackschleife mit Rückfragen
- Docs-Code für graphische Darstellungen
- 2D-Welt / Levelstruktur

### Einordnung

Diese Punkte gehören primär zu Projektorganisation, Prototyping und Dokumentation.

### Kategorie

- **Feature:** Visualisierungen in Docs, z. B. Mermaid-Diagramme.
- **Feature:** Levelstruktur zum Einführen von Spell-Makros.
- **Offene Frage:** Engine-Wahl für 2D-Prototyp und spätere 3D-/Steam-Tauglichkeit.
- **Festgelegt:** Die Zusammenarbeit soll weiterhin über Rohnotizen → Clusterung → Rückfragen → Docs/Issues laufen.

---

## 2. Biologische Mana-Quellen und Opferlogik

### Kernaussage

Wenn biologische oder chemisch gebundene Energie als Mana-Quelle dienen kann, ergeben sich Tier- oder Menschenopfer als morbides, aber logisch ableitbares Ritualmotiv.

### Abgleich mit bestehendem Stand

Dies passt zu DD-003:

> ATP bzw. chemisch/biologisch gebundene Energie ist nicht Mana selbst, sondern eine mögliche Quelle für magische Arbeit.

### Kategorie

- **Beispiel:** Tier- oder Menschenopfer als biologische Mana-Quelle.
- **Hypothese:** Popkulturelle Ritualmotive können emergent aus dem Energie-/Mana-Modell entstehen.
- **Offene Frage:** Wie wird biologische Energieentnahme mechanisch, ethisch und spielerisch modelliert?

### Hinweis

Das Beispiel ist inhaltlich morbide, aber systemisch nützlich, weil es zeigt, dass bekannte Fantasy-/Okkultismusmotive nicht hardcodiert werden müssen, sondern aus Grundregeln entstehen können.

---

## 3. Energieumwandlung: normale Energie ↔ Mana

### Kernaussage

Normale Energiequellen sollten in Mana-Arbeit übertragbar sein, und Mana sollte wieder in normale Energieformen überführt werden können.

### Kategorie

- **Hypothese:** Energie und Mana-Arbeit sind umrechenbar oder zumindest koppelbar.
- **Offene Frage:** Gibt es eine direkte Mana-Joule-Umrechnung?
- **Offene Frage:** Welche Verluste entstehen bei Energie→Mana und Mana→Energie?

---

## 4. Weltmaterialität: Pixel-/Block-basierte 2D-Welt

### Kernaussage

Die 2D-Welt soll vorzugsweise pixel- oder zellbasiert sein, aber mit flüssigen Bewegungsvektoren statt nur Bewegung entlang einer groben x/y-Achse.

Alle Materialien sollen grundsätzlich manipulierbar, bewegbar, zerstörbar und transformierbar sein.

### Kategorie

- **Hypothese:** Pixel-/Zellwelt ist geeignete Basis für 2D-Prototyp.
- **Feature:** deformierbare, zerstörbare, transformierbare Materialwelt.
- **Offene Frage:** Wie wird Performance bei Explosionen, vielen bewegten Pixeln und Kollisionen gesichert?

---

## 5. Homogene Darstellung vs. innere Zusammensetzung

### Kernaussage

Kompositmaterialien wie Stein werden als homogene Masse angezeigt, solange sie nicht analysiert oder getrennt werden.

Intern können sie aus mehreren Stoffen, Molekülen oder Elementfraktionen bestehen.

Beispiel:

```text
Stein = Quarz/Silikate + Sauerstoff + Spurenelemente + Salze/Metalle
```

### Kategorie

- **Hypothese:** Materialien haben eine sichtbare Makroform und eine interne Zusammensetzung.
- **Feature:** Analyse- und Trennzauber können interne Zusammensetzung sichtbar machen.
- **Begriff:** Materialauflösung, Fraktion, Zusammensetzung, Stoffgemisch.

---

## 6. Element-, Stoff- und Materialkataloge

### Kernaussage

Die Welt braucht mehrere Ebenen von Materialbeschreibung:

```text
Element → Stoff/Molekül/Substanz → Material → natürliches Objekt
```

### Attribute

Materialien sollten Parameter besitzen wie:

- Härte
- Dichte
- Leitfähigkeit
- Entflammbarkeit
- Säure-/Laugenempfindlichkeit
- Magnetismus
- Reflektivität
- Elastizität / Bounciness
- Flexibilität
- Reibung
- Viskosität
- Gefrierpunkt / Siedepunkt
- Bruchmodus
- chemische Energie / Reaktivität / Elektronegativität

### Kategorie

- **Feature:** Elementkatalog.
- **Feature:** Material-/Substanzkatalog.
- **Feature:** Natürliche Objektbibliothek.
- **Begriff:** Materialattribut, Substanz, Fraktion, Stoffgemisch.

---

## 7. Vorgeschlagene Elemente

### Vorschlag aus Rohnotizen

Nützlicher funktionaler Element-Cutoff statt vollständiges Periodensystem.

Genannt wurden:

```text
H, He?, Ar, C, N, P, O, S, Cl, Na, Ca, Mg?, Fe, Cu, Ag, Au, Pt,
Pb, Hg?, U, Al?, Ti?, Li?, Si, F?, K?, Sn?, Zn?, W?
```

### Kategorie

- **Hypothese:** Es braucht keinen vollständigen Elementkatalog, sondern eine funktional ausreichende Auswahl.
- **Offene Frage:** Welche Elemente sind für Gameplay, Materiallogik und Zauber wirklich nötig?

---

## 8. Natürliche Objekte und heterogene Materialien

### Kernaussage

Die Welt braucht erweiterbare natürliche Objektdefinitionen, die aus heterogenen Materialien bestehen.

Beispiele:

| Objekt | Bestandteile |
|---|---|
| Gestein | Quarz/Silikate, Eisen, Kupfer, Silber, Gold, Platin, Salze |
| Baum | photosynthetisches Gewebe, Meristem, Holz, Rinde |
| Luft | Stickstoff, Sauerstoff, Argon, Wasserdampf, CO₂ |

### Kategorie

- **Feature:** Objektdefinitions-Bibliothek.
- **Feature:** Natürliche Materialklassen.
- **Offene Frage:** Wie detailliert müssen natürliche Objekte intern modelliert werden?

---

## 9. Phasenmodell und Feuer

### Kernaussage

Die Welt sollte mindestens vier Phasen modellieren:

```text
fest, flüssig, gasförmig, Plasma
```

Feuer ist kein Grundelement. Magisches Feuer wäre physikalisch eher Plasma, Hitze, Lichtemission und chemische Reaktion.

### Kategorie

- **Festgelegt/Hypothese:** Feuer soll nicht als Element behandelt werden.
- **Feature:** Phasenmodell.
- **Offene Frage:** Welche Aspekte von Plasma müssen wirklich simuliert werden?

---

## 10. Felder, Elektrizität, Magnetismus, Säuren/Laugen

### Kernaussage

Neben Materie und Wärme sollten auch elektrische und magnetische Phänomene sowie chemische Reaktionen wie Säuren/Laugen berücksichtigt werden.

### Kategorie

- **Feature:** Strom/Elektrizität.
- **Feature:** Magnetfelder.
- **Feature:** Säuren/Laugen-Chemie.
- **Offene Frage:** Werden Felder als eigene Entitäten, als Zellattribute oder als globale Felder modelliert?

---

## 11. Größe physischer Zauberrepräsentationen

### Kernaussage

Die Größe einer gemalten/gravierten Zauberstruktur könnte Effizienz, Präzision oder maximale Leistung beeinflussen.

Kleiner gezeichnete Zauber auf Artefakten könnten eine Mana-Penalty haben, besonders wenn sie deutlich kleiner als das Zielobjekt oder die Wirkungsgröße sind.

### Kategorie

- **Hypothese:** Repräsentationsgröße beeinflusst Effizienz/Präzision/Kosten.
- **Offene Frage:** Ist die Größe absolut, relativ zur Wirkung oder abhängig vom Detailgrad?

---

## 12. Schwebendes Licht und Grundsatzfrage der Lichterzeugung

### Kernaussage

Ein schwebendes Licht könnte unterschiedlich modelliert werden:

1. Luft-Plasma durch Energieeintrag.
2. erhitztes materielles Medium, z. B. Metall oder Staubpartikel.
3. direkte Erzeugung/Emission von Lichtwellen.

### Zentrale Frage

Kann Magie nur energetisch auf Materie einwirken, oder kann sie intrinsische physikalische Phänomene wie elektromagnetische Wellen direkt erzeugen?

### Kategorie

- **Beispiel:** Schwebendes Licht.
- **Offene Frage:** Braucht Lichterzeugung ein Medium oder kann Magie direkt Photonen/EM-Wellen erzeugen?
- **Offene Frage:** Ist Magie nur Materiemanipulation oder auch Feld-/Wellenmanipulation?

---

## 13. Materialanalyse

### Kernaussage

Ein „Material-Zusammensetzung-Analyser“ könnte entweder eine inhärente Spielerfähigkeit oder ein eigener Zauber sein.

### Kategorie

- **Feature:** Materialanalyse.
- **Offene Frage:** Ist Analyse Grundfähigkeit, Skill, Zauber, Artefaktfunktion oder UI-Hilfe?
- **Gameplay:** Analyse könnte progressiv Detailtiefe freischalten, damit Spieler nicht überfordert werden.

---

## 14. Informationsverarbeitung als Zauberkomponente

### Kernaussage

Bestimmte Komponenten wie Suchen, Sortieren, Sammeln, Trennen, Ausweichen, Anziehen oder Abstoßen wirken eher wie Informationsverarbeitung als reine physische Arbeit.

Beispiel:

Ein fliegendes Licht, das Kollisionen vermeidet, braucht nicht nur Bewegung, sondern auch Wahrnehmung/Prüfung/Entscheidungslogik.

### Kategorie

- **Begriff:** Informationskomponente, Kontrollkomponente, Intelligenzkomponente.
- **Hypothese:** Informationsverarbeitung kostet weniger Mana als Bewegung oder Transformation.
- **Offene Frage:** Wird Informationsverarbeitung über Mana, kognitive Kontrolle, Komplexität oder eigene Rechenkosten bepreist?

---

## 15. Progressive Analyse und unbekannte Restfraktionen

### Kernaussage

Um Spieler nicht zu überfordern, könnten Materialanalysen anfangs nur grobe Hauptbestandteile anzeigen und Restfraktionen als unbekannt zusammenfassen.

Beispiel:

```text
Luft: 78% Stickstoff, 21% Sauerstoff, 2% unbekannter Rest
```

### Kategorie

- **Gameplay:** Progressive Offenlegung von Materialdetails.
- **Feature:** Analyselevel / Wissensprogression.

---

## 16. Sub-Pixel-Fraktionen und Materialauflösung

### Kernaussage

Wenn Stoffanteile weniger als ein Pixel Volumen einnehmen würden, sollen sie nicht verloren gehen. Stattdessen können mehrere Sub-Pixel-Fraktionen denselben Pixelraum überlagern, solange ihr gemeinsames Volumen unterhalb eines Pixelvolumens bleibt.

### Kategorie

- **Feature:** Sub-Pixel-Fraktionen.
- **Hypothese:** Überlagerte Fraktionspixel erhalten Masse ohne sichtbare Kollision.
- **Offene Frage:** Wie werden solche Fraktionen bei Trennung, Bewegung und Kollision behandelt?

---

## 17. Performance, Explosionen und Kollisionen

### Kernaussage

Eine pixelbasierte, vollständig manipulierbare Welt kann bei Explosionen, vielen Vektoren und Kollisionen schnell teuer werden.

### Kategorie

- **Simulation:** Performance-Optimierung.
- **Offene Frage:** Welche Spatial-Partitioning-, Chunking- oder LOD-Mechanismen sind nötig?
- **Feature:** Cutoffs und Aggregationsmodelle für Wärme, Gase, Flüssigkeiten und Partikel.

---

## 18. Memory-Slots für häufige Makros

### Kernaussage

Spieler sollten eine begrenzte Anzahl häufig verwendeter Zauber-Makros memorisieren können.

Diese Makros können dann ohne mitgeführte Referenzbibliothek rekonstruiert werden, solange die physische Repräsentation neu erzeugt wird, z. B. mit Tinte auf Papier oder einem Stock in Sand/Erde.

### Abgleich mit bestehendem Stand

Dies ergänzt das Hybridmodell aus `docs/14_spell_libraries_and_references.md`.

### Kategorie

- **Feature:** Memory-Slots für gelernte Makros.
- **Gameplay:** Komfort, Skillprogression, Inventarentlastung.
- **Offene Frage:** Welche Komplexität kann memorisiert werden?

---

## 19. Hierarchische Verteilung von Wärme, Flüssigkeiten und Gasen

### Kernaussage

Wärme, Flüssigkeiten und Gase sollen nicht unendlich detailliert simuliert werden. Stattdessen wird mit räumlichen Cutoffs gearbeitet:

```text
lokal präzise → regional aggregiert → globaler Wert
```

Ziel:

- Performance sparen
- Massen-/Energieerhaltung erhalten
- lokale Effekte präzise halten
- globale Bilanz fortführen
- geschlossene Räume/Container korrekt behandeln

### Kategorie

- **Feature:** Hierarchisches LOD-/Aggregationsmodell.
- **Festgelegt/Hypothese:** Keine Materialverluste durch Vereinfachung.
- **Offene Frage:** Wie werden geschlossene Räume und Container erkannt?

---

## 20. Redundanzen

| Neue Notiz | Bereits abgedeckt durch |
|---|---|
| Engine-Wahl | Issue #9 |
| Feedbackschleife | bisherige Projektarbeitsweise |
| Biologische Opfer als Manaquelle | DD-003, OQ-007 |
| Energie ↔ Mana | OQ-006 |
| Memory-Slots | `docs/14_spell_libraries_and_references.md`, aber jetzt präzisiert |
| Visuelle Repräsentation / Zaubergröße | DD-007, `docs/13_visual_spell_language.md` |

## 21. Neue relevante Entscheidungen/Fragen

1. Weltauflösung: Pixel, Zelle, Block oder Hybrid?
2. Materialmodell: Element → Substanz → Material → Objekt.
3. Feuer ist kein Grundelement, sondern Prozess/Plasma/Licht/Wärme.
4. Feld-/Wellenmanipulation muss geklärt werden.
5. Materialanalyse braucht Progression und Detailstufen.
6. Sub-Pixel-Fraktionen müssen massenerhaltend modelliert werden.
7. Wärme/Gase/Flüssigkeiten brauchen LOD-Aggregation ohne Erhaltungsverlust.
8. Informationskomponenten brauchen eigenes Kostenmodell.
