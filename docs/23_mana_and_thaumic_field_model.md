# 23 — Mana and Thaumic Field Model

**Status:** Arbeitsmodell / Grundhypothese nach DD-010  
**Bezug:** `docs/05_energy_costs_limits.md`, `docs/07_design_decisions.md`, `docs/12_focus_media_and_artifacts.md`, `docs/15_material_world_model.md`

---

## 1. Zweck

Dieses Dokument präzisiert, was Mana im System ontologisch und simulationstechnisch bedeutet.

Die Leitfrage lautet:

```text
Wie kann Mana als magische Arbeitsressource existieren,
ohne Energie aus dem Nichts zu erzeugen
und ohne Mana als eigenen Stoff oder eigenes Teilchen einzuführen?
```

---

## 2. Grundentscheidung

Mana ist **kein Stoff**, **kein Element** und **kein Mana-Partikel**.

Mana bezeichnet die nutzbare magische Arbeit, die über eine thaumische Kopplungsschicht aus realen physikalischen Energiepotentialen verfügbar gemacht werden kann.

```text
Mana = nutzbarer thaumischer Arbeitsfluss aus realen Energiepotentialen
```

Die Welt besitzt dafür ein thaumisches Analog zu realen Energiepotentialen:

```text
physikalisches Energiepotential
→ gekoppeltes thaumisches Potential
→ Zaubergeometrie koppelt daran
→ magische Arbeit
→ physikalische Quelle entlädt sich + Verluste
```

Keine Energie wird erschaffen oder vernichtet. Das thaumische Feld ist eine Übertragungs- und Kopplungsebene, keine zusätzliche Gratisenergiequelle.

---

## 3. Thaumisches Feldpotential

Jedes reale Energiepotential kann ein thaumisches Analog besitzen.

| Physikalische Seite | Thaumische Seite |
|---|---|
| elektrische Spannung | thaumische Spannung |
| chemisches Potential | thaumisches Reaktionspotential |
| gespannte Feder | thaumisches mechanisches Potential |
| Temperaturgradient | thaumisches Wärmegefälle |
| bewegtes Wasser / Wind | thaumischer Arbeitsfluss |
| biologische Stoffwechselenergie | bio-thaumisches Potential |
| geladene Batterie | gekoppelte thaumische Entladefähigkeit |

Wichtig:

```text
Thaumisches Potential ist keine zusätzliche Energie.
Es ist eine magisch adressierbare Zugriffsebene auf reale Energieunterschiede.
```

Eine Entladung des thaumischen Potentials entlädt daher zugleich die gekoppelte physikalische Quelle.

Beispiel:

```text
Batterie geladen
→ elektrische Spannung vorhanden
→ thaumisches Analog vorhanden
→ Zaubergeometrie koppelt an thaumisches Potential
→ Zauberarbeit wird verrichtet
→ Batterie entlädt sich + Verlustwärme
```

---

## 4. Zaubergeometrie als reales Gerät

Physische Zauberrepräsentationen sind nicht nur symbolische Hinweise auf eine abstrakte Datenstruktur.

Sie wirken zugleich als reale thaumische Geräte:

```text
Zaubergeometrie = Schaltkreis / Antenne / Linse / Ventil / Transformator
                  für thaumische Potentiale
```

Eine gültige Zaubergeometrie kann:

- ein thaumisches Potential anzapfen
- Flussrichtung bestimmen
- Kopplung an Quelle und Ziel herstellen
- Entladung begrenzen
- Wirkungskanal formen
- Verluste reduzieren oder verlagern
- Zielzustände präzisieren
- Abbruch- oder Sicherheitsbedingungen tragen

Dadurch wird die physische visuelle Repräsentation bedeutungsstärker:

```text
Zauberbild ≠ bloßes Symbol
Zauberbild = materiell vorhandene Kopplungsstruktur
```

---

## 5. Mana-Speicher

Mana-Speicher enthalten keine Mana-Substanz und keine Mana-Partikel.

Sie speichern einen metastabilen thaumischen Potentialzustand.

```text
geladener Mana-Speicher = Materialstruktur
                         + gespeicherte physikalische/thaumische Potentialkonfiguration
                         + Stabilisierung durch Struktur, Material oder Geometrie
```

Analogie:

| Elektrisches / physikalisches Modell | Thaumisches Modell |
|---|---|
| Kondensator speichert Ladungstrennung | Kristall speichert thaumische Potentialtrennung |
| Batterie speichert chemisches Potential | Artefakt speichert gekoppelte Energie-/Feldkonfiguration |
| Spule speichert Feldenergie | Ritualstruktur speichert gerichteten thaumischen Fluss |
| Leckstrom | Mana-Leckage |
| Durchschlag | thaumische Überladung / Rückkopplung / Strukturbruch |

Ein Kristall ist also nicht deshalb nützlich, weil er Energie erzeugt, sondern weil er ein geladenes thaumisches Potential stabil halten kann.

```text
Kristall erzeugt keine Energie.
Kristall hält nutzbare thaumische Spannung stabil.
```

---

## 6. Materialattribute für Mana

Materialien können thaumische Eigenschaften besitzen.

| Attribut | Bedeutung | Status |
|---|---|---|
| `mana_capacity` | Maximale speicherbare thaumische Arbeit / Potentialmenge. | Hypothese |
| `mana_charge` | Aktuell gespeicherte thaumische Ladung bzw. nutzbare Arbeit. | Hypothese |
| `thaumic_potential` | Aktuelle thaumische Spannung / Potentialhöhe. | Hypothese |
| `mana_conductivity` | Wie gut thaumischer Fluss durch das Material läuft. | Hypothese |
| `mana_leakage` | Wie schnell gespeichertes Potential verloren geht. | Hypothese |
| `mana_conversion_efficiency` | Wie gut reale Energie in nutzbaren thaumischen Arbeitsfluss gekoppelt wird. | Hypothese |
| `mana_discharge_rate` | Wie schnell gespeichertes Potential sicher abgegeben werden kann. | Hypothese |
| `mana_overload_threshold` | Grenze, ab der Material, Fokus oder Zauber instabil wird. | Hypothese |
| `syntax_affinity` | Wie gut ein Material physische Zaubergeometrie trägt oder verstärkt. | Hypothese |
| `feedback_risk` | Risiko einer Rückkopplung in Speicher, Fokusmedium oder Zauberer. | Hypothese |

Diese Attribute sind keine endgültige Engine-Schnittstelle, aber ein gutes frühes Vokabular für Materialdesign, Artefakte und Prototyping.

---

## 7. Mögliche Materialrollen

| Materialtyp | Mögliche thaumische Rolle |
|---|---|
| Kristall | Hohe Kapazität, geringe Leckage, gute Potentialstabilität. |
| Metall | Gute Leitung, hohe Entladerate, eventuell hohes Rückkopplungsrisiko. |
| Organisches Gewebe | Gute Bio-Konversion, instabiler Langzeitspeicher. |
| Fett / Öl | Hohe chemische Energiequelle, aber nicht automatisch guter Mana-Speicher. |
| Blut | Bio-chemische Quelle, mögliche Ziel-/Identitätsbindung, instabil und gefährlich. |
| Holz | Gute physische Zaubergeometrie, gute Handhabung, geringe Rückkopplung. |
| Knochen / Horn | Mögliche stabile Ritual- oder Symbolbindung. |
| Wasser | Gute biologische Verteilung, schwache langfristige Speicherung. |

Diese Rollen sind Hypothesen. Sie sollen später aus Materialattributen, nicht aus Fantasy-Konventionen, abgeleitet werden.

---

## 8. Energiequellen und thaumische Nutzung

Jede reale Energiequelle kann prinzipiell als Mana-Quelle dienen, wenn passende Kopplungsgeometrie, Materialstruktur und Zielsyntax vorhanden sind.

Beispiele:

```text
Flussbewegung
→ Turbine / mechanische Rotation
→ physikalisches Arbeitsgefälle
→ thaumisches Feldpotential
→ Zaubergeometrie koppelt daran
→ Mana-Speicher wird geladen oder Zauber direkt betrieben
```

```text
Fett / Zucker / biologische Materie
→ chemische Reaktion / Stoffwechselentzug
→ bio-thaumisches Potential
→ Zauberarbeit
→ Erschöpfung + Wärme + Nebenprodukte
```

```text
geladene Batterie
→ elektrische Spannung
→ thaumische Spannung
→ Zaubergeometrie entlädt Quelle kontrolliert
→ magische Arbeit + elektrische/thermische Nebenfolgen
```

```text
gespannte Feder
→ mechanisches Potential
→ thaumisches mechanisches Analog
→ Entladung über Zaubergeometrie
→ Feder entspannt sich + magische Arbeit + Verluste
```

---

## 9. Das Batteriepack-Zauberer-Problem

Ein streng energieerhaltendes System erzeugt natürlich die Frage, warum mächtige Zauberer nicht immer große Batterien, Brennstoffe oder Maschinen mit sich tragen müssen.

Dieses Problem wird nicht vollständig wegdefiniert. Es ist eine erwünschte Systemgrenze.

### 9.1 Effizienz statt Energiemasse

Gute Zauberer sind nicht nur große Energiespeicher, sondern finden energetische Hebelpunkte.

```text
Tür öffnen ≠ Tür sprengen
kleine Verriegelung bewegen → großer Effekt
```

```text
Feuer erzeugen ≠ Haus verbrennen
kleine Zündenergie → vorhandenes Brennmaterial übernimmt
```

```text
Felssturz auslösen ≠ Felsen erschaffen
kleine Stabilitätsänderung → Gravitation liefert Hauptarbeit
```

```text
Gegner stolpern lassen ≠ Gegner durch Raum schleudern
kleine Gleichgewichtsstörung → Körperdynamik erledigt Rest
```

### 9.2 Körpermagie mit harter Leistungsgrenze

Ein Zauberer ist nie vollständig ohne Mana, solange er biologische Energie besitzt.

```text
Körperenergie
→ bio-thaumische Kopplung
→ Zauberarbeit
→ Erschöpfung + Unterzuckerung + Wärme + Stoffwechselstress
```

Mögliche Übernutzungsfolgen:

| Übernutzung | Folge |
|---|---|
| kurzfristiger Energieentzug | Schwäche, Zittern, Konzentrationsverlust |
| hoher Leistungsabruf | Überhitzung, Kreislaufstress |
| tiefer Bio-Entzug | Gewebeschaden, Bewusstlosigkeit |
| extremer Entzug | Nekrose, Organversagen, Tod |
| instabile Kopplung | Rückkopplung in Nerven, Muskeln oder Blut |

### 9.3 Infrastruktur und Artefakte

Große oder häufige Zauber benötigen gespeicherte Energie, Infrastruktur oder Umweltquellen.

```text
Kraftwerk / Ritual / Opfer / Sonne / Fluss / Verbrennung
→ lädt Kristall oder Artefakt langsam auf
→ Zauberer trägt kompakten Speicher
→ schnelle Entladung unterwegs
```

Kurz:

```text
Infrastruktur lädt.
Zauberer entlädt.
```

---

## 10. Emergente Zauberer-Typen

Aus dem Energie- und Speicherproblem ergeben sich unterschiedliche Spiel- und Weltrollen.

| Typ | Energiemodell | Mögliche Rolle |
|---|---|---|
| Kampfzauberer | Trägt geladene Speicher, Foki oder Infrastrukturzugang. | Hohe Leistung, hohe Logistikabhängigkeit. |
| Stealth-Zauberer | Nutzt kleine, effiziente Zauber und lokale Hebelpunkte. | Geringe Signatur, wenig Ausrüstung. |
| Ritualmagier | Nutzt stationäre Quellen, Vorbereitung und langsame Kopplung. | Große Effekte, geringe Mobilität. |
| Artefaktmagier | Verlässt sich auf geladene Werkzeuge und vorbereitete Strukturen. | Flexibel, aber abhängig von Ausrüstung. |
| Bio-Magier | Nutzt Körperenergie oder biologische Quellen. | Immer handlungsfähig, aber gesundheitlich riskant. |
| Infrastrukturmagier | Arbeitet mit Maschinen, Kraftwerken, Turbinen oder städtischen Quellen. | Mächtig im vorbereiteten Umfeld. |

Diese Typen sind keine festen Klassen. Sie entstehen aus Energiemodell, Materialzugang, Speicherqualität und Zauberstil.

---

## 11. Zauberstab als emergentes Kompositwerkzeug

Ein Zauberstab ist kein pauschales Bonus-Item.

Er ist ein Komposit aus Materialrollen:

```text
Zauberstab = Leiter + Speicherzugang + Geometrieträger + Zielantenne + Sicherheitsfilter
```

Möglicher Aufbau:

```text
Holzschaft:
  gute Handhabung
  geringe Rückkopplung
  gut gravierbar

Metalladern:
  hohe mana_conductivity
  gerichteter Fluss

Kristallkern:
  mana_capacity
  mana_charge
  Entladungspuffer

Gravuren:
  Zaubersyntax / Kontrollgeometrie

Spitze:
  Zielbindung / Flussfokussierung
```

Daraus folgt:

```text
Körper allein:
  gute Bioquelle
  schlechte Präzision
  hohes Rückkopplungsrisiko

Zauberstab:
  stabiler Kanal
  bessere Zielrichtung
  geringere Leckage
  definierte Entladerate
  eingravierte Syntax
```

---

## 12. Simulation als Zustandsgrößen

Im 2D-Prototyp sollte Mana nicht als Partikelsystem simuliert werden.

Stattdessen können Weltzellen, Objekte oder Artefakte zusätzliche thaumische Zustandsgrößen tragen.

Beispiel:

```text
WorldCell:
  material_fractions
  temperature
  pressure
  velocity
  charge_distribution
  thaumic_potential
  mana_capacity
  mana_charge
  mana_conductivity
  mana_leakage
  mana_conversion_efficiency
```

Für normale Weltzellen können viele Werte niedrig oder null sein. Für Kristalle, Artefakte, Ritualflächen oder besondere Materialien können sie hoch oder spezialisiert sein.

Zauberausführung:

```text
SpellExecution:
  required_work
  available_mana
  source_potential
  coupling_efficiency
  conversion_efficiency
  discharge_rate
  control_noise
  target_resistance
  heat_loss
  failure_modes
```

---

## 13. Fehlerfälle

Fehler sollen weiterhin bevorzugt emergent entstehen.

| Fehlerfall | Ursache |
|---|---|
| Quelle entlädt sich zu schnell | Entladerate überschritten. |
| Zauber verpufft | Zu wenig `available_mana` oder schlechte Kopplung. |
| Fokus überhitzt | Verlustwärme oder hoher Durchfluss. |
| Kristall bricht | `mana_overload_threshold` überschritten. |
| Rückkopplung | Fluss läuft in Speicher, Fokus oder Körper zurück. |
| Wirkung streut | Geometrie oder Zielbindung unpräzise. |
| Quelle kollabiert | Physikalisches Analog wurde entladen oder zerstört. |
| Bio-Schaden | Körperenergie wird zu schnell oder zu tief entzogen. |

---

## 14. Festgelegt, verworfen, offen

### Festgelegt

- Mana ist keine Substanz und kein Teilchen.
- Mana ist an reale Energiepotentiale gekoppelt.
- Eine thaumische Entladung entlädt zugleich die physikalische Quelle.
- Physische Zaubergeometrien wirken als reale Kopplungsstrukturen.
- Mana-Speicher speichern metastabile thaumische Potentialzustände.
- Energie-, Massen- und Impulserhaltung bleiben gültig.

### Verworfen

- Mana-Partikel als Standardmodell.
- Mana als eigenständiges Element.
- Mana als Energie aus dem Nichts.

### Offen

- Gibt es eine direkte Mana-Joule-Umrechnung?
- Wie exakt wird `thaumic_potential` aus physikalischen Energiepotentialen berechnet?
- Welche Materialien haben welche Mana-Attribute?
- Wie wird Kopplungsgeometrie im Parser und in der Simulation repräsentiert?
- Wie stark hängt Kopplung von Material, Form, Größe, Präzision und Beschädigung ab?
- Wie werden Mana-Leckage, Überladung und Rückkopplung numerisch simuliert?

---

## 15. Arbeitsdefinition

```text
Mana = nutzbarer thaumischer Arbeitsfluss aus realen Energiepotentialen.

Thaumisches Potential = gekoppelte Feldspannung, die aus physikalischen
Energieunterschieden hervorgeht.

Mana-Speicher = Materialstruktur, die thaumisches Potential metastabil bindet.

Zaubergeometrie = physische Syntaxstruktur, die thaumisches Potential koppelt,
richtet, transformiert und auf Zielzustände anwendet.
```
