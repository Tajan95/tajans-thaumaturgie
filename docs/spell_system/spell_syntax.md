# 03 — Spell Syntax

**Stand:** 2026-07-14, 01:44 Europe/Berlin  
**Status:** Arbeitsmodell / Issue #2 teilweise geklärt

## Zweck

Dieses Dokument beschreibt, wie ein Zauber formal aufgebaut sein könnte.

Die zentrale Frage lautet:

> Aus welchen syntaktischen Bestandteilen besteht ein Zauber?

Issue #2 ist noch nicht vollständig entschieden. Geklärt sind inzwischen zwei notwendige Submodelle:

1. Aktivierung und Beendigung eines Zaubers
2. Zielauswahl und atomare Zustandswirkungen

Details siehe:

- `spell_lifecycle_and_activation.md`
- `target_and_effect_node_model.md`

---

## Vorläufiges Schema

```text
Zauber := Aktivierung / Start
        + Zielauswahl und Zielbindung
        + atomare Wirkung(en)
        + Struktur / räumliche Anwendung
        + Modifier
        + Kosten / Energiequelle / Kopplung
        + Bedingungen und Informationslogik
        + Kontrollanforderung
        + Ausführungs- und Beendigungslogik
        + Fehlerlogik / Failsafe
        + physische visuelle Repräsentation
```

Dieses Schema ist noch kein finales Datenmodell. Es beschreibt die Mindestbereiche, die ein Zauber formal abbilden können muss.

---

## Komponenten

| Komponente | Funktion | Beispiel |
|---|---|---|
| Aktivierung / Start | Bestimmt, wann und wie der Zauber ausgeführt wird. | sofort bei Fertigstellung, bei Wort, bei Geste, bei Kontakt |
| TargetNode | Erzeugt eine explizite, typisierte Zielmenge. | Wasserzellen im Kreis, dieser Stein, CO₂-Fraktion in Luft |
| EffectNode | Fordert eine atomare Zustandsoperation an. | Wärme übertragen, Kraft anwenden, Stoffmasse transportieren |
| Struktur | Bestimmt räumliche Form und Verteilung. | Linie, Kreis, Kegel, Oberfläche, Volumenbereich |
| Modifier | Verändert Parameter oder Policies. | verstärken, umkehren, verzögern, limitieren |
| Kosten / Energiequelle / Kopplung | Beschreibt Aufwand, Quelle und Zugriff auf thaumisches Potential. | Körperenergie, Kristall, Artefakt, Umweltwärme, Fokusmedium |
| Bedingung / Information | Legt Auslöse-, Auswahl-, Gültigkeits- oder Laufzeitlogik fest. | bei Kontakt, Material = Wasser, solange sichtbar |
| Kontrollanforderung | Beschreibt mentale, thaumische oder motorische Ausführungslast. | Konzentration, Timing, Präzision, Haltegeste |
| Ausführungs- und Beendigungslogik | Beschreibt, ob der Zauber einmalig, gehalten, autonom, getoggelt oder wiederholt läuft. | One-Shot, while-held, toggle, loop |
| Fehlerlogik / Failsafe | Beschreibt Abbrüche, Limits oder Fehlwirkungen. | Energiemangel, Zielverlust, Überhitzung |
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

Verzögerungen, Vokalisierung, Gestik, Scharfschaltung, Umweltbedingungen oder Sicherheitsmechanismen sind explizite Anweisungen, keine stillschweigenden Defaults.

---

## Aktuelle Teilentscheidung: TargetNode

Ein TargetNode definiert keine Wirkung. Er erzeugt ein typisiertes `TargetSet`.

```text
TargetNode {
    selector
    anchor
    scope
    filters[]
    granularity
    binding_mode
    update_policy
    access_constraints[]
    failure_policy
    output: TargetSet
}
```

Mögliche Zielreferenzen:

```text
ObjectRef
CellRef
CellRegionRef
SurfaceRef
MaterialFractionRef
PointRef
BiologicalRegionRef
```

Dadurch können sowohl ganze Objekte als auch lokale Zellbereiche oder Stofffraktionen innerhalb eines Gemischs adressiert werden.

### Bindungsmodus

```text
snapshot
```

bindet die Zielmenge zu einem definierten Zeitpunkt.

```text
live
```

wertet sie während der Laufzeit erneut aus und verursacht höhere Such-, Bindungs- und Steuerkosten.

---

## Aktuelle Teilentscheidung: EffectNode

Ein primitiver EffectNode enthält genau eine atomare Zustandsoperation.

```text
EffectNode {
    domain
    operation
    target_inputs: Map<TargetRole, TargetSet>
    parameters
    application_mode
    timing
    precision_requirement
    resource_binding
    output: StateChangeRequest[]
}
```

Beispiele für primitive Operationen:

```text
ApplyForce
ApplyTorque
TransferThermalEnergy
TransferCharge
TransportComponentMass
ChangeBondStructure
RequestPhaseTransition
ChangeNuclearComposition
```

Eine atomare Transferoperation darf mehrere physikalisch gekoppelte Zustandsdeltas erzeugen, etwa Wärmeabnahme an einer Quelle und Wärmezunahme an einer Senke.

---

## Effect-Domänen

Vorläufige Standarddomänen:

- mechanisch-kinematisch
- mechanisch-strukturell
- thermisch
- elektrisch in Materie
- kompositionell / transportbezogen
- chemisch
- phasenbezogen
- nuklear

Informationsoperationen wie Suchen, Erkennen, Klassifizieren oder Filtern werden als eigene Query-/Analysis-Node-Familien behandelt.

Biologische oder kognitive Zauber sind keine elementaren Standardprimitive. Sie müssen aus materiellen, chemischen, elektrischen und informationsverarbeitenden Operationen abgeleitet werden.

---

## Zielrollen

Ein EffectNode kann mehrere benannte Zielports benötigen:

```text
subject
source
recipient
source_location
destination
reference_frame
energy_source
energy_sink
byproduct_sink
```

Beispiel Wärmetransfer:

```text
source: zu kühlendes Wasser
recipient / energy_sink: Umgebung oder Speicher
```

Beispiel Stofftrennung:

```text
source: Luftgemisch
subject: CO₂-Fraktion
destination: Sammelgefäß
```

---

## Parallelität

Mehrere primitive EffectNodes dürfen parallel ausgeführt werden.

```text
              ┌→ ApplyForce
Activation ───┤
              └→ TransferThermalEnergy
```

Parallele Operationen lesen vorläufig denselben Tick-Ausgangszustand. Ihre Änderungsanträge werden anschließend gemeinsam auf Konflikte, Ressourcen und Erhaltung geprüft und erst danach committed.

Kompakte Multi-Effekt-Zauber werden als Makros über solchen Teilgraphen dargestellt. Für Kosten und Validierung wird der Makrograph vollständig expandiert.

---

## StateChangeRequest

EffectNodes verändern die Welt nicht unmittelbar. Sie erzeugen prüfbare Änderungsanträge.

```text
StateChangeRequest {
    operation_id
    target_refs[]
    state_deltas[]
    requested_rate_or_duration
    physical_minimum_work_J
    control_work_J
    source_requirements[]
    sink_requirements[]
    byproducts[]
    conservation_constraints[]
    precision_requirement
    failure_policy
}
```

Die Regelengine kann einen Antrag vollständig zulassen, begrenzen, verschieben, abbrechen oder ablehnen.

---

## Energie- und Steuerkosten

Die Kosten eines EffectNodes werden dynamisch aus Operation, Zielzustand und Parametern berechnet.

```text
Gesamtarbeit =
    physikalische Effektarbeit
  + Zielerfassung und Zielbindung
  + Steuer- und Präzisionsarbeit
  + Kopplungsverluste
  + Sicherheits- und Prüfoperationen
  + kontinuierliche Laufzeitkosten
  + Nebenproduktbehandlung
```

Jede primitive Operation kann einen Basiskostenanteil besitzen. Die Kosten hängen jedoch nicht von der sichtbaren Anzahl der Editor-Knoten ab, sondern vom expandierten internen Graphen.

```text
sichtbarer MacroNode
→ expandierter Teilgraph
→ Kosten aller ausgeführten primitiven Operationen
```

---

## Vorläufige interne Form

Die aktuellen Teilentscheidungen stützen folgende starke Hypothese:

```text
Interne Zauberform = Komponentenobjekt + typisierter gerichteter Wirkungsgraph
```

```text
Spell {
    representation
    activation_nodes[]
    graph {
        target_nodes[]
        query_and_analysis_nodes[]
        effect_nodes[]
        control_nodes[]
        resource_nodes[]
        safety_nodes[]
        edges[]
    }
    execution_policy
    termination_policy
    failure_model
}
```

Begründung:

- Ein reines Sequenzmodell ist für parallele Wirkungen und Ressourcenflüsse zu starr.
- Ein reiner Syntaxbaum ist für Zielbindungen, Transfers und kontinuierliche Effekte möglicherweise zu hierarchisch.
- Ein freier Graph wäre ohne typisierte Knoten und Komponentenrahmen zu beliebig.
- Ein typisierter Wirkungsgraph verbindet Editor, Parser, Validierung, Kostenmodell und Simulation.

---

## Minimaler Zauber

Ein minimaler Zauber braucht mindestens:

```text
ActivationNode
+ TargetNode
+ EffectNode
+ Energiequelle / Ressourcenmodell
+ physische Repräsentation
+ Fehlerverhalten bei Ungültigkeit
```

Defaultwerte:

```text
trigger: on_completion_of_start_glyph
mode: execute_once
binding_mode: snapshot
resource_binding: prepay_required_cost
termination: after_sequence
failure: abort_if_invalid_or_unpayable
```

---

## Beispiel: Wasser um 10 K erwärmen

```text
Activation:
    on_complete_execute_once

TargetNode:
    MaterialSelector(Wasser)
    innerhalb einer definierten Kreisfläche
    binding_mode: snapshot

EffectNode:
    TransferThermalEnergy
    delta_temperature: +10 K

ResourceNode:
    gebundener Energiespeicher oder Körperquelle
```

Die Regelengine bestimmt aus Wassermasse, Wärmekapazität, Ausgangstemperatur, Kopplung und Verlusten die erforderliche Energie in Joule.

---

## Syntaxfehler und Laufzeitfehler

| Fehlertyp | Beschreibung | Beispiel |
|---|---|---|
| Syntaxfehler | Struktur oder Portverbindung ist formal ungültig. | Temperaturwert mit Objektport verbunden |
| Semantikfehler | Struktur ist formal korrekt, aber widersprüchlich. | dieselbe Masse gleichzeitig vollständig an zwei Orte transportieren |
| Zielbindungsfehler | TargetSet ist leer, mehrdeutig oder nicht zugänglich. | Live-Ziel außerhalb der Reichweite |
| Ressourcenfehler | Zauber ist gültig, aber nicht bezahlbar. | zu wenig Energie im Speicher |
| Referenzfehler | Bibliothek, Quelle oder Repräsentation fehlt. | Runenfragment zerstört |
| Aktivierungsfehler | Startbedingungen fehlen oder sind nicht erfüllt. | Vokaltrigger nicht erkannt |
| Laufzeitfehler | Bedingungen ändern sich während der Ausführung. | Zielbindung bricht |
| Konfliktfehler | parallele StateChangeRequests sind nicht gemeinsam erfüllbar. | widersprüchliche Positionsdeltas |
| Terminationsfehler | Zauber endet nicht sauber. | autonomer Quellenlauf ohne Limit |

Fehler sollen bevorzugt emergent aus der konkreten Zauberstruktur entstehen.

---

## Offene Fragen

1. Ist das Hybridmodell aus Komponentenobjekt und typisiertem Graph die finale interne Form?
2. Können mehrere ActivationNodes in einem Zauber existieren?
3. Welche TargetRef-Typen braucht der erste Prototyp?
4. Welche Filter und Query-Nodes sind Grundprimitive und welche bibliotheksabhängig?
5. Wie werden widersprüchliche parallele StateChangeRequests aufgelöst?
6. Darf ein EffectNode bei Energiemangel teilweise ausgeführt werden?
7. Welche atomaren Effect-Operationen bilden die minimale Standardbibliothek?
8. Wie werden visuelle Syntaxfehler diagnostiziert?
9. Wann ist eine physische Repräsentation beschädigt, aber noch teilweise ausführbar?
