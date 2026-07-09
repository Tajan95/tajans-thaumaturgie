# 12 — Focus Media and Artifacts

Dieses Dokument sammelt die frühe Theorie zu Zauberstäben, Fokusmedien, Mana-Speichern, Ritualen und Artefakten.

**Status:** Arbeitsmodell / Feature-Sammlung  
**Bezug:** DD-010 und `docs/23_mana_and_thaumic_field_model.md`

---

## Fokusmedium

Ein Fokusmedium ist ein Werkzeug, das magische Operationen präziser, effizienter oder stabiler macht.

Nach DD-010 ist ein Fokusmedium nicht nur ein symbolisches Hilfsmittel, sondern eine materielle Kopplungsstruktur für thaumische Potentiale.

Vorläufige Beispiele:

- Zauberstab
- Ring
- Stab mit Kristallkern
- Ritualkreis
- stationäres Artefakt
- tätowierte oder gravierte Zauberstruktur

## Grundfunktionen eines Fokusmediums

| Funktion | Bedeutung |
|---|---|
| Leitung | Führt thaumischen Arbeitsfluss mit geringerem Verlust. |
| Speicherzugang | Bindet geladene Kristalle oder andere Mana-Speicher an die Zaubergeometrie. |
| Kopplung | Verbessert die Verbindung zwischen physikalischer Energiequelle, thaumischem Potential und Zauberstruktur. |
| Zielantenne | Verbessert Zielbindung, Reichweite oder Richtung. |
| Linse | Bündelt, formt oder fokussiert thaumische Wirkung. |
| Sicherheitsfilter | Reduziert Streuung, Rückkopplung und Fehlentladung. |
| Repräsentationsträger | Kann visuelle Zaubersyntax tragen, z. B. Gravuren oder eingelassene Muster. |
| Entladeregler | Begrenzt, wie schnell gespeichertes Potential abfließt. |

## Zauberstab

Ein Zauberstab ist ein tragbares Fokusmedium.

Er ist kein pauschales Bonus-Item, sondern ein Kompositwerkzeug:

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

## Mana-Speicher

Mana-Speicher ermöglichen Zugriff auf gespeicherte magische Arbeit.

Nach DD-010 speichern sie keine Mana-Substanz und keine Mana-Partikel. Sie halten metastabile thaumische Potentialzustände.

```text
geladener Mana-Speicher = Materialstruktur
                         + gespeicherte physikalische/thaumische Potentialkonfiguration
                         + Stabilisierung durch Struktur, Material oder Geometrie
```

Mögliche Eigenschaften:

| Eigenschaft | Bedeutung |
|---|---|
| `mana_capacity` | Maximale speicherbare thaumische Arbeit / Potentialmenge. |
| `mana_charge` | Aktuell gespeicherte thaumische Ladung bzw. nutzbare Arbeit. |
| `thaumic_potential` | Aktuelle thaumische Spannung / Potentialhöhe. |
| `mana_conductivity` | Wie gut thaumischer Fluss durch das Material läuft. |
| `mana_leakage` | Wie schnell gespeichertes Potential verloren geht. |
| `mana_conversion_efficiency` | Wie gut reale Energie in nutzbaren thaumischen Arbeitsfluss gekoppelt wird. |
| `mana_discharge_rate` | Wie schnell gespeichertes Potential sicher abgegeben werden kann. |
| `mana_overload_threshold` | Grenze, ab der Material, Fokus oder Zauber instabil wird. |
| `syntax_affinity` | Wie gut ein Material physische Zaubergeometrie trägt oder verstärkt. |
| `feedback_risk` | Risiko einer Rückkopplung in Speicher, Fokusmedium oder Zauberer. |

## Biologische und nicht-biologische Quellen

Da Mana als thaumischer Arbeitsfluss aus realen Energiepotentialen definiert ist, können sowohl biologische als auch nicht-biologische Quellen relevant sein.

| Quelle | Beschreibung |
|---|---|
| Lebewesen | chemisch/biologisch gebundene Energie wird magisch nutzbar gemacht |
| biologische Materie | kann als Brennstoff oder Opfermaterial dienen |
| Kristall | speichert metastabile thaumische Spannung |
| Artefakt | speichert Energie, Struktur, Zielbindung oder Auslösebedingungen |
| Umgebung | Wärme, Licht, Bewegung, Wind, Wasser, elektrische Infrastruktur oder andere Energieformen |
| Maschine | Turbine, Generator, Federwerk, Batterie oder andere technische Energiequelle |

## Artefakte

Artefakte können Energie, Zaubersyntax, Zielbindung oder Auslösebedingungen speichern.

Mögliche Funktionen:

- gespeicherten Zauber ausführen
- Effekt dauerhaft stabilisieren
- Ritual automatisieren
- externe Manaquelle verwalten
- visuelle Repräsentation dauerhaft tragen
- physikalische Energiequellen thaumisch koppeln
- thaumische Spannung puffern oder dosiert abgeben
- Nutzer vor Rückkopplung schützen

Artefakte können dadurch als mobile Speicher, Schalter, Konverter, Sicherheitsfilter oder autonome Zaubergeräte funktionieren.

## Rituale

Rituale sind vorbereitete oder räumlich stabilisierte Zauberprozesse.

Sie können helfen bei:

- hoher Komplexität
- langer Dauer
- mehreren Beteiligten
- großem Energiebedarf
- genauer Zielbindung
- stabiler physischer Repräsentation
- langsamer, effizienter Aufladung von Speichern
- sicherer Kopplung an große Energiequellen

Kurzmodell:

```text
Infrastruktur lädt.
Artefakt speichert.
Zauberer entlädt.
```

## Emergente Zauberer-Typen

Aus Fokusmedien, Speichern und Energiequellen ergeben sich mögliche Spielstile, ohne feste Klassen hardzucoden.

| Typ | Energiemodell | Mögliche Rolle |
|---|---|---|
| Kampfzauberer | Trägt geladene Speicher, Foki oder Infrastrukturzugang. | Hohe Leistung, hohe Logistikabhängigkeit. |
| Stealth-Zauberer | Nutzt kleine, effiziente Zauber und lokale Hebelpunkte. | Geringe Signatur, wenig Ausrüstung. |
| Ritualmagier | Nutzt stationäre Quellen, Vorbereitung und langsame Kopplung. | Große Effekte, geringe Mobilität. |
| Artefaktmagier | Verlässt sich auf geladene Werkzeuge und vorbereitete Strukturen. | Flexibel, aber abhängig von Ausrüstung. |
| Bio-Magier | Nutzt Körperenergie oder biologische Quellen. | Immer handlungsfähig, aber gesundheitlich riskant. |
| Infrastrukturmagier | Arbeitet mit Maschinen, Kraftwerken, Turbinen oder städtischen Quellen. | Mächtig im vorbereiteten Umfeld. |

## Offene Fragen

1. Speichert ein Artefakt Energie, Syntax, Zielbindung oder mehrere getrennte Komponenten?
2. Welche Materialkombinationen ergeben gute Zauberstäbe, schlechte Zauberstäbe oder gefährliche Zauberstäbe?
3. Können Fokusmedien verschleißen?
4. Gibt es gefährliche Rückkopplung zwischen Magier und Mana-Speicher?
5. Sind Rituale langsamere, aber effizientere Zauber?
6. Können biologische Mana-Quellen ethisch, mechanisch oder physisch gefährlich sein?
7. Welche Materialien eignen sich für dauerhafte visuelle Zauberrepräsentationen?
8. Wie werden `mana_capacity`, `mana_conductivity`, `mana_leakage` und `mana_overload_threshold` konkret berechnet?
9. Können beschädigte Fokusmedien thaumische Spannung unkontrolliert freisetzen?
