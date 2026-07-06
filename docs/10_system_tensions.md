# 10 — System Tensions

Dieses Dokument sammelt logische Spannungspunkte, die aus den ersten Rohnotizen erkennbar wurden.

Ein Spannungspunkt ist noch kein harter Widerspruch. Er zeigt aber eine Stelle, an der das System später eine klare Entscheidung oder saubere Unterscheidung braucht.

---

## W-001 — Mana als ATP vs. Mana als universelles Energieäquivalent

ATP ist eine biologische Energieeinheit und damit körpergebunden. Ein universelles Mana-Modell muss aber auch Kristalle, Rituale, Artefakte und nicht-biologische Energiequellen erklären.

### Auflösung

ATP bzw. chemisch/biologisch gebundene Energie ist nicht Mana selbst, sondern nur eine mögliche biologische Quelle für magische Arbeit.

Mana wird als abstrakter Energie-/Arbeitsbegriff behandelt.

### Status

Geklärt durch DD-003.

---

## W-002 — Beliebige Zauber vs. Erhaltungsgesetze

Das Projektziel spricht davon, beliebige denkbare Zauber formal ausdrücken zu können. Gleichzeitig sollen Energie, Masse und Impuls erhalten bleiben.

### Auflösung

„Beliebig“ bedeutet kombinatorisch offen, nicht physikalisch unbegrenzt.

Ein Zauber kann nur dann gültig sein, wenn er Quellen, Senken, Kosten, Nebenprodukte, Zielbezug und Erhaltungssätze erfüllt.

### Status

Geklärt durch DD-004.

---

## W-003 — LLM-Ergänzung vs. formale Präzision

Ein LLM kann unausgesprochene Bedeutungen ergänzen, aber genau dadurch die formale Strenge des Systems untergraben.

### Auflösung

Das LLM darf nur Hilfsmittel sein. Die Regelengine validiert, ob der Zauber syntaktisch korrekt, semantisch gültig, bezahlbar und simulierbar ist.

### Status

Geklärt durch DD-005.

---

## W-004 — Makros als ineffizient vs. Makros als Expertenoptimierung

Vorgefertigte Zauberkomponenten könnten ineffizient sein, wenn sie generisch sind. Sie könnten aber effizienter sein, wenn sie von Experten optimiert wurden.

### Auflösung

Makro-Effizienz ist emergent.

Generische Einsteiger-Makros enthalten oft Overhead und sind bequem, aber nicht optimal. Experten-Makros können sehr effizient sein, wenn sie gut optimiert sind.

### Status

Geklärt durch DD-006.

---

## W-005 — Zauberstab optional vs. dauerhaft überlegen

Wenn Magie ohne Zauberstab möglich ist, aber Zauberstäbe selbst bei maximaler Erfahrung überlegen bleiben, muss klar sein, warum.

### Mögliche Auflösung

Der Körper kann Magie ausführen, aber ein Fokusmedium reduziert Streuung, Verlust und Kontrollrauschen ähnlich wie ein optisches Instrument.

### Status

Hypothese. Muss im Fokusmedien-Modell weiter ausgearbeitet werden.

---

## W-006 — Physische visuelle Repräsentation vs. abstrakte Datenstruktur

Zauber sollen in-world physisch und visuell existieren. Technisch müssen sie aber als Datenstruktur, Graph oder Programm simuliert werden.

### Auflösung

Beides ist notwendig:

```text
visuelle Repräsentation ↔ Parser/Visualizer ↔ abstrakte Zauberstruktur ↔ Regelengine
```

Ein korrekt gezeichneter Zauber muss korrekt in Programmlogik übersetzbar sein. Ein abstrakt programmierter Zauber muss in eine gültige physische/visuelle Repräsentation übersetzbar sein, um in-world ausführbar zu werden.

### Status

Geklärt als Grundentscheidung durch DD-007. Technische Ausarbeitung offen.

---

## W-007 — Emergent falsche Zauber vs. abstrakte Misslingen-Modifier

Fehler sollen bevorzugt emergent aus falscher Syntax, ungültigen Referenzen, fehlender Energie oder instabiler Kontrolle entstehen. Für ein Spiel könnten aber zusätzliche Misslingen-Modifier nützlich sein.

### Mögliche Auflösung

Emergente Fehler sind Standard. Abstrakte Misslingen-Modifier werden nur dort eingeführt, wo Simulation, Gameplay oder UI sonst unnötig schwerfällig werden.

### Status

Offen.
