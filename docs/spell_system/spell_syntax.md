# 03 — Spell Syntax

**Stand:** 2026-07-13, 18:18 Europe/Berlin  
**Status:** Arbeitsmodell / Issue #2 teilweise geklärt

## Zweck

Dieses Dokument beschreibt, wie ein Zauber formal aufgebaut sein könnte.

Die zentrale Frage lautet:

> Aus welchen syntaktischen Bestandteilen besteht ein Zauber?

Issue #2 ist damit noch nicht vollständig entschieden. Geklärt ist aber ein erstes notwendiges Submodell: Zauber brauchen eine Aktivierungs- und Beendigungslogik.

Details siehe:

- `spell_lifecycle_and_activation.md`

---

## Vorläufiges Schema

```text
Zauber := Aktivierung / Start
        + Ziel
        + Wirkung
        + Struktur
        + Modifier
        + Kosten / Energiequelle / Kopplung
        + Bedingung
        + Kontrollanforderung
        + Ausführungs- und Beendigungslogik
        + Fehlerlogik / Failsafe
        + physische visuelle Repräsentation
```

Dieses Schema ist noch kein finales Datenmodell. Es beschreibt die Mindestbereiche, die ein Zauber irgendwann formal abbilden können muss.

---

## Komponenten

| Komponente | Funktion | Beispiel |
|---|---|---|
| Aktivierung / Start | Bestimmt, wann und wie der Zauber ausgeführt wird. | sofort bei Fertigstellung, bei Wort, bei Geste, bei Kontakt |
| Ziel | Bestimmt, worauf der Zauber wirkt. | Objekt, Fläche, Richtung, Lebewesen, Materialklasse |
| Wirkung | Bestimmt, was verändert wird. | erhitzen, bewegen, binden, trennen |
| Struktur | Bestimmt die Form der Wirkung. | Linie, Kreis, Kegel, Punkt, Feld |
| Modifier | Verändert Parameter der Wirkung. | verstärken, umkehren, verzögern, limitieren |
| Kosten / Energiequelle / Kopplung | Beschreibt Aufwand, Quelle und Zugriff auf thaumisches Potential. | Körperenergie, Kristall, Artefakt, Umweltwärme, Fokusmedium |
| Bedingung | Legt Auslöse-, Gültigkeits- oder Laufzeitlogik fest. | bei Kontakt, solange sichtbar, nach Zeit, bis Temperaturgrenze |
| Kontrollanforderung | Beschreibt mentale oder motorische Ausführungslast. | Konzentration, Timing, Präzision, Haltegeste |
| Ausführungs- und Beendigungslogik | Beschreibt, ob der Zauber einmalig, gehalten, autonom, getoggelt oder wiederholt läuft. | One-Shot, while-held, toggle, loop, until-resource-depleted |
| Fehlerlogik / Failsafe | Beschreibt mögliche Abbrüche oder Fehlwirkungen. | Energiemangel, ungültiges Ziel, Syntaxfehler, Überhitzung |
| Visuelle Repräsentation | Macht den Zauber in-world ausführbar. | Schriftrolle, Gravur, Tattoo, Ritualkreis |

---

## Aktuelle Teilentscheidung: Start-Glyphe und Default-Ausführung

Jeder ausführbare Zauber besitzt mindestens eine **Start-Glyphe** bzw. einen **Activation Node**.

Ohne expliziten Start-Modifier gilt:

```text
on_complete_execute_once
```

Das bedeutet:

> Sobald die Start-Glyphe vollständig und gültig fertiggestellt ist, versucht der Zauber, sich einmal auszuführen.

Diese Default-Regel ist bewusst streng. Verzögerungen, Vokalisierung, Gestik, Scharfschaltung, Umweltbedingungen oder Sicherheitsmechanismen sind explizite Anweisungen, keine stillschweigenden Defaults.

---

## Vorläufige interne Form

Für den aktuellen Arbeitsstand ist ein reines Sequenz-, Baum- oder Graphmodell noch nicht entschieden.

Die Start-/Stop-Logik legt aber nahe, dass ein Zauber zumindest als Komponentenobjekt mit verknüpften Teilstrukturen gedacht werden muss:

```text
Spell {
    representation
    activation_node
    target_model
    effect_model
    structure_model
    modifier_model
    resource_model
    execution_policy
    termination_policy
    failure_model
}
```

Ob `effect_model`, `target_model` und `structure_model` intern als Graph, Syntaxbaum, Sequenz oder Hybrid dargestellt werden, bleibt weiterhin Gegenstand von Issue #2.

Aktuelle starke Hypothese:

```text
Interne Zauberform = Komponentenobjekt + gerichteter Wirkungsgraph
```

Begründung:

- Ein reines Sequenzmodell ist für parallele Wirkungen, Bedingungen und Ressourcenflüsse zu starr.
- Ein reiner Syntaxbaum ist für Rückkopplungen, Zielbindungen und kontinuierliche Effekte möglicherweise zu hierarchisch.
- Ein freier Graph ist mächtig, aber ohne Komponentenrahmen zu beliebig.
- Ein Komponentenobjekt mit internen Graphstrukturen könnte Validierung, Editor und Simulation besser verbinden.

---

## Minimaler Zauber

Ein minimaler Zauber braucht mindestens:

```text
Start-Glyphe
+ Ziel
+ Wirkung
+ Energiequelle / Ressourcenmodell
+ physische Repräsentation
+ Fehlerverhalten bei Ungültigkeit
```

Der einfachste Fall verwendet Defaultwerte:

```text
trigger: on_completion_of_start_glyph
mode: execute_once
resource_binding: prepay_required_cost
termination: after_sequence
failure: abort_if_invalid_or_unpayable
```

---

## Beispiel als abstrakte Form

```text
Aktivierung: Start-Glyphe fertiggestellt
Ziel: Wasserfläche
Wirkung: Temperatur senken
Struktur: Kreisfläche
Modifier: Dauer 10 Sekunden
Kosten: proportional zu Fläche und Temperaturdifferenz
Energiequelle: Kristall oder Körper
Nebenprodukt: abgeführte Wärme
Beendigung: nach 10 Sekunden oder bei Ressourcenmangel
Repräsentation: gezeichneter Kreiszauber auf Trägermedium
Ergebnis: lokale Vereisung, wenn Wärmeabfuhr und Kosten gedeckt sind
```

---

## Syntaxfehler und Laufzeitfehler

Ein Zauber verhält sich analog zu einem Programm.

| Fehlertyp | Beschreibung | Beispiel |
|---|---|---|
| Syntaxfehler | Die Struktur ist formal ungültig. | fehlender Zielblock, unverbundener Modifier |
| Semantikfehler | Die Struktur ist formal korrekt, aber bedeutungslos oder widersprüchlich. | `erhitze` + `senke Temperatur` ohne Priorität |
| Ressourcenfehler | Der Zauber ist gültig, aber nicht bezahlbar. | zu wenig Mana im Speicher |
| Referenzfehler | Eine benötigte Quelle, Bibliothek, Bindung oder Repräsentation fehlt. | Runenfragment zerstört, Kristall entfernt |
| Aktivierungsfehler | Der Zauber ist gültig, aber Startbedingungen fehlen oder sind nicht erfüllt. | Vokaltrigger fehlt, Umweltbedingung nicht erfüllt |
| Laufzeitfehler | Während der Ausführung ändern sich Bedingungen. | Ziel verlässt Bereich, Fokus bricht |
| Terminationsfehler | Der Zauber endet nicht sauber oder hat keine sichere Abschaltung. | autonomer Quellenlauf ohne Limit |

Fehler sollen bevorzugt emergent aus der konkreten Zauberstruktur entstehen. Abstrakte Misslingen-Modifier bleiben vorläufig offen.

---

## Offene Fragen

1. Werden Zauber final eher als lineare Sequenz, Graph, Syntaxbaum, Komponentenobjekt oder Hybridmodell modelliert?
2. Können mehrere Wirkungen parallel in einem Zauber laufen?
3. Können mehrere Aktivierungsknoten in einem Zauber existieren?
4. Wie wird Zielauswahl formal definiert?
5. Wie werden visuelle Syntaxfehler erkannt und diagnostiziert?
6. Wann ist eine physische Repräsentation beschädigt, aber noch teilweise ausführbar?
7. Wie werden Schleifen, Bedingungen und Informationskomponenten begrenzt, damit keine allwissenden Zauber entstehen?
