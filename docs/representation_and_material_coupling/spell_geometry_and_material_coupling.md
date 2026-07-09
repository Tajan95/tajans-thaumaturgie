# 24 — Spell Geometry and Material Coupling

**Status:** Arbeitsmodell / Grundentscheidung nach DD-011  
**Bezug:** `docs/07_design_decisions.md`, `docs/23_mana_and_thaumic_field_model.md`, `docs/05_energy_costs_limits.md`, `docs/12_focus_media_and_artifacts.md`

---

## 1. Zweck

Dieses Dokument präzisiert, wie physische Zauberrepräsentationen mit Materialeigenschaften zusammenwirken.

Leitfrage:

```text
Muss eine Zaubergeometrie aus thaumisch leitfähigem Spezialmaterial bestehen,
oder reicht jede stabile geometrische Form in bzw. auf Materie?
```

---

## 2. Grundentscheidung

Zaubergeometrie kann grundsätzlich **additiv**, **subtraktiv** oder **hybrid** realisiert werden.

```text
Additiv:
  Material wird aufgetragen.
  Beispiel: Tinte, Kreide, Asche, Metallpulver.

Subtraktiv:
  Material wird entfernt, verdrängt oder verformt.
  Beispiel: Kratzer, Gravur, Schnitt, Furche, Rille, Hohlraum.

Hybrid:
  Material wird entfernt und anschließend gefüllt, beschichtet oder eingefasst.
  Beispiel: Metallfüllung in Holzgravur, Kristallstaub in Steinrille.
```

Eine Zauberrepräsentation muss daher nicht zwingend aus Spezialtinte bestehen.

Entscheidend ist eine stabile, präzise und materiell realisierte Geometrie, die vom System als gültige Zaubersyntax geparst und als thaumische Kopplungsstruktur genutzt werden kann.

```text
Geometrie bestimmt Gültigkeit.
Material bestimmt Kopplungsqualität.
```

---

## 3. Positive und negative Zaubergeometrie

### Positive Zaubergeometrie

Positive Zaubergeometrie entsteht durch aufgetragenes Material.

Beispiele:

- Tinte auf Papier
- Kreide auf Stein
- Asche auf Holz
- Metallpulver auf Keramik
- Kristallstaub in Bindemittel

Vorteile:

- schnell herstellbar
- leicht veränderbar
- Material kann gezielt gewählt werden
- gut für temporäre Zauber

Nachteile:

- verwischbar
- abhängig von Haftung und Trägermaterial
- Linienmaterial kann verbrennen, reißen, abplatzen oder auslaufen

### Negative Zaubergeometrie

Negative Zaubergeometrie entsteht durch entfernte oder verformte Materie.

Beispiele:

- in Erde gezogener Kreis
- Kratzer in Stein
- Gravur in Metall
- Schnitt in Holz
- in Sand gezogene Linie

Vorteile:

- braucht kein Spezialmaterial
- kann dauerhaft sein
- nutzt direkt die Eigenschaften des Trägermaterials
- erlaubt improvisierte Magie

Nachteile:

- abhängig von Kantenpräzision und Materialstabilität
- bei Erde oder Sand leicht zerstörbar
- schwer zu ändern
- kann bei Überlastung brechen, splittern oder ausglühen

### Hybrid-Zaubergeometrie

Hybridformen kombinieren subtraktive Formgebung mit additiver Füllung oder Beschichtung.

Beispiele:

```text
Holzgravur + Metallader
Steinrille + Kristallstaub
Metallgravur + isolierende Keramikmasse
```

Diese Formen sind besonders interessant für Artefakte, Zauberstäbe und hochwertige Ritualkreise.

---

## 4. Grenzflächenmodell für negative Geometrie

Negative Zaubergeometrien funktionieren nicht, weil Luft ein guter thaumischer Leiter wäre.

Normale Luft ist im Standardmodell eher ein schwaches thaumisches Zwischenmedium bzw. Dielektrikum.

Der Kopplungseffekt entsteht durch:

```text
Material-Luft-Grenzfläche
+ Hohlraumform
+ Kantenpräzision
+ geometrische Kontinuität
+ Trägermaterialstabilität
```

Kurz:

```text
Subtraktive Zaubergeometrie koppelt über Grenzflächen, nicht über gute Luftleitung.
```

Eine Rille erzeugt einen Materialkontrast und eine definierte Grenzfläche. Diese Grenzfläche kann einen schwachen thaumischen Oberflächen- oder Hohlraumkanal bilden.

```text
glatte Oberfläche
→ kaum definierte Kopplungsbahn

eingeritzte Rille
→ Materialunterbrechung
→ Luftfüllung oder anderes Füllmedium
→ scharfe Grenzflächen
→ schwacher thaumischer Kopplungskanal
```

---

## 5. Luft als Füllmedium

Luft soll im Standardmodell **kein guter thaumischer Leiter** sein.

Begründung:

```text
Wenn Luft gut thaumisch leitfähig wäre,
wäre die gesamte Atmosphäre ein ständig verfügbarer thaumischer Leiter.
```

Das hätte problematische Folgen:

- Fernwirkung würde schwerer begrenzbar.
- Zauber könnten stärker streuen.
- Mana-Leckage in die Umgebung wäre hoch.
- Materialkanäle, Gravuren und Spezialtinten würden an Bedeutung verlieren.
- Die Materialökonomie von Fokusmedien und Artefakten würde geschwächt.

Daher gilt:

```text
Luft = schwaches Füll- und Zwischenmedium
nicht = guter thaumischer Leiter
```

Mögliche Abstufung:

| Medium | Thaumische Rolle |
|---|---|
| Vakuum | sehr schlechte Standardkopplung |
| trockene Luft | schwaches Füllmedium, hohe Streuung |
| feuchte Luft / Nebel | etwas bessere Kopplung, aber unpräziser |
| Rauch / Staub / Aschepartikel | bessere Kopplung durch Partikel, aber instabil |
| ionisierte Luft / Plasma | deutlich bessere Kopplung, aber energieintensiv und riskant |
| Spezialtinte | gezielt optimierte Kopplung |
| Metallpulver / Metallader | gute Leitung, Rückkopplungsrisiko |
| Kristallstaub | Stabilisierung / Speicherung / Resonanz |

---

## 6. Materialeinfluss

Zaubermaterialien beeinflussen nicht primär, **ob** ein Zauber logisch existiert, sondern **wie gut** er koppelt.

```text
Syntaxgültigkeit = primär Geometrie / Zeichen / Struktur
Kopplungsqualität = Geometrie + Material + Grenzfläche + Stabilität
```

Mögliche Einflussgrößen:

| Faktor | Bedeutung |
|---|---|
| `geometry_validity` | Ist die Form syntaktisch gültig? |
| `geometry_precision` | Wie präzise sind Winkel, Linien, Abstände und Proportionen? |
| `line_material.syntax_affinity` | Wie gut trägt das Linienmaterial Zaubersyntax? |
| `line_material.mana_conductivity` | Wie gut leitet das aufgetragene Material thaumischen Fluss? |
| `substrate_material.stability` | Wie stabil ist das Trägermaterial während der Wirkung? |
| `substrate_material.mana_leakage` | Wie stark verliert das Trägermaterial thaumisches Potential? |
| `boundary_contrast` | Wie stark ist der Material- oder Strukturkontrast an der Linie? |
| `edge_precision` | Wie scharf und kontinuierlich sind Kanten, Rillen oder Schnitte? |
| `fill_medium_factor` | Wie gut unterstützt das Füllmedium im Hohlraum die Kopplung? |
| `integrity` | Wie vollständig und unbeschädigt ist die Repräsentation? |
| `scale_factor` | Passt die Größe der Geometrie zur gewünschten Wirkung? |

---

## 7. Vorläufige Kopplungsformeln

### Allgemeine Kopplung

```text
effective_coupling =
    geometry_validity
  × geometry_precision
  × material_factor
  × boundary_factor
  × substrate_stability
  × integrity
  × scale_factor
```

### Additive Geometrie

```text
additive_geometry_coupling =
    geometry_validity
  × geometry_precision
  × line_material.syntax_affinity
  × line_material.mana_conductivity
  × line_material.adhesion
  × substrate_compatibility
  × integrity
```

### Subtraktive Geometrie

```text
negative_geometry_coupling =
    geometry_validity
  × edge_precision
  × boundary_contrast
  × void_continuity
  × fill_medium_factor
  × substrate_stability
  × integrity
```

### Sichere Entladerate

```text
safe_mana_flow = min(
    geometry_max_flow,
    line_or_boundary_conductivity,
    substrate_material.mana_overload_threshold,
    source_discharge_rate,
    focus_or_storage_discharge_rate
)
```

---

## 8. Beispiele

| Repräsentation | Typ | Erwartete Kopplung |
|---|---|---|
| Kreis in Erde | subtraktiv | schwach, instabil, improvisierbar |
| Tinte auf Papier | additiv | alltagstauglich, mittlere Stabilität |
| Metallhaltige Tinte | additiv | leitfähiger, höhere Entladerate, riskanter |
| Gravur in Stein | subtraktiv | dauerhaft, stabil, gut für Rituale |
| Gravur in Metall | subtraktiv / hybrid | stark leitend, überlastungsanfällig |
| Zauberstabgravur | subtraktiv / hybrid | stabiler Kanal, gute Integration mit Fokusmedium |

---

## 9. Fehlerfälle

| Fehlerfall | Ursache |
|---|---|
| Zauber verpufft | Geometrie gültig, aber Kopplung zu schwach. |
| Effekt streut | Kanten, Linien oder Materialkontraste sind unpräzise. |
| Linie verbrennt | Manafluss überschreitet Materialbelastung. |
| Rille bricht aus | Substrat kann Spannung oder Wärme nicht tragen. |
| Tinte verläuft | Integrität der positiven Geometrie geht verloren. |
| Erde verwischt | Negative Geometrie verliert Kontinuität. |
| Metallrückkopplung | Leitfähigkeit hoch, Sicherheitsfilter schlecht. |
| Überhitzung | Verluste werden nicht abgeführt. |
| semantischer Kollaps | Geometrie ist materiell vorhanden, aber syntaktisch widersprüchlich. |

---

## 10. Konsequenzen

### Festgelegt

- Spezialtinte ist nützlich, aber nicht zwingend.
- Additive und subtraktive Zaubergeometrien können beide gültig sein.
- Luft ist kein guter thaumischer Leiter.
- Luftgefüllte Hohlräume können dennoch über Grenzflächen schwach koppeln.
- Materialwahl beeinflusst Kopplungseffizienz, Entladerate, Stabilität, Leckage, Überlastungsrisiko und Fehlerverhalten.

### Gameplay-Folgen

- Magie bleibt improvisierbar.
- Hochwertige Materialien bleiben relevant.
- Schwache Notfallzauber bleiben möglich.
- Artefakte, Zauberstäbe und Ritualkreise werden durch Materialoptimierung stärker.
- Formen wie Runensteine, Kreidekreise, Ritzungen, Gravuren und Tattoos bleiben erklärbar.

### Weltbau-Folgen

- Magierbedarf erzeugt Märkte für Spezialtinten, leitfähige Pigmente, Kristallstaub, Gravurmaterialien und stabile Träger.
- Alte Gravuren können noch thaumisch aktiv oder gefährlich sein.
- Beschädigte Ritualkreise können durch Materialfehler statt durch abstraktes Pech versagen.
- Architektur kann thaumisch relevante Linienführung enthalten.

---

## 11. Offene Fragen

1. Welche Mindestqualität braucht eine Geometrie, um überhaupt als gültig zu gelten?
2. Welche Materialien haben hohe `syntax_affinity`?
3. Wie stark soll schlechte Kopplung Kosten erhöhen, statt den Zauber komplett scheitern zu lassen?
4. Können absichtlich schlechte Materialien als Sicherheitsdrossel verwendet werden?
5. Wie werden verschmierte, gebrochene oder teilweise verdeckte Zeichen geparst?
6. Können Hohlräume mit bestimmten Gasen, Staub, Rauch oder Flüssigkeiten gezielt verbessert werden?
7. Wie stark beeinflusst die Größe einer Rille oder Linie die maximale Entladerate?
8. Gibt es Materialien, die thaumisch isolierend genug sind, um Zauber bewusst zu blockieren?
