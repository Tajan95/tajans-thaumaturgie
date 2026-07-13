# Spell Lifecycle and Activation

**Stand:** 2026-07-13, 18:18 Europe/Berlin  
**Status:** Teilentscheidung / Arbeitsmodell für Issue #2

Dieses Dokument beschreibt, wie ein Zauber gestartet, gehalten, wiederholt, beendet und abgebrochen wird.

Es behandelt nicht die gesamte interne Form eines Zaubers, sondern nur das erste notwendige Submodell:

```text
Activation & Termination Model
= Wie wird ein Zauber scharfgeschaltet, gestartet, gehalten und beendet?
```

---

## 1. Grundsatz

Jeder ausführbare Zauber besitzt mindestens einen **Aktivierungsknoten** bzw. eine **Start-Glyphe**.

Die Start-Glyphe ist nicht nur ein dekoratives Startzeichen, sondern der Einstiegspunkt in die Ausführung des Zauberprogramms.

```text
Start-Glyphe = Entry Point / Activation Node
```

Ohne zusätzlichen Start-Modifier gilt der einfachste Standardfall:

```text
on_complete_execute_once
```

Das bedeutet:

> Sobald die Start-Glyphe vollständig und gültig fertiggestellt ist, versucht der Zauber, sich einmal auszuführen.

Das ist bewusst der Default. Verzögerungen, Vokalisierung, Gestik, Umweltbedingungen, Scharfschaltung oder Sicherheitsmechanismen sind keine impliziten Annahmen, sondern müssen als explizite Start- oder Sicherheitsmodifier im Zauber vorhanden sein.

---

## 2. Fertigstellung und Ausführung

Für das Modell wird trotzdem logisch zwischen Fertigstellung, Validierung und Ausführung unterschieden.

```text
1. Repräsentation wird erstellt
2. Start-Glyphe wird abgeschlossen
3. Zauber wird geparst
4. Zauber wird validiert
5. Default oder explizite Startlogik wird ausgewertet
6. Ausführung beginnt
7. Ausführung läuft einmalig, gehalten, autonom oder wiederholt
8. Ausführung endet oder wird abgebrochen
9. Cleanup / Restzustand
```

Im einfachsten Fall fallen mehrere dieser Schritte praktisch zusammen:

```text
Start-Glyphe fertig → gültig → sofortige Einmalausführung
```

Bei vorbereiteten, getriggerten oder ritualisierten Zaubern bleiben sie getrennt:

```text
Zauber fertig → gültig → armed → wartet auf Trigger → Ausführung
```

---

## 3. Aktivierungsknoten als Datenstruktur

Vorläufiges Arbeitsmodell:

```text
ActivationNode {
    trigger_condition
    start_conditions
    activation_mode
    resource_binding
    execution_policy
    termination_policy
    cooldown_or_rearm_policy
    failure_policy
}
```

### Felder

| Feld | Bedeutung | Beispiel |
|---|---|---|
| `trigger_condition` | Was startet den Zauber? | Fertigstellung, Wort, Geste, Kontakt, Zeit, Umweltbedingung |
| `start_conditions` | Was muss vor dem Start wahr sein? | Ziel vorhanden, Quelle verfügbar, kein Vakuum, Temperaturbereich gültig |
| `activation_mode` | Wie wird der Zauber nach dem Start geführt? | einmalig, gehalten, Toggle, autonom, wiederholt |
| `resource_binding` | Wie wird Mana/Energie gebunden oder gezogen? | Vorabzahlung, Reservierung, Dauerverbrauch, gebundene Quelle |
| `execution_policy` | Wie läuft die Wirkung ab? | einmalig, kontinuierlich, Schleife/Puls |
| `termination_policy` | Wann endet der Zauber? | nach Sequenz, bei Loslassen, nach Dauer, bei Bedingung, bei Ressourcenende |
| `cooldown_or_rearm_policy` | Wann darf der Zauber erneut starten? | sofort, nach Zeit, nach Neuladen, nach manueller Reaktivierung |
| `failure_policy` | Was passiert bei Fehlern? | abbrechen, entkoppeln, entladen, fehlwirken, Sicherheitsabschaltung |

---

## 4. Minimaler Zauber

Ein minimaler ausführbarer Zauber kann intern so gedacht werden:

```text
Spell {
    representation
    activation_node
    target_model
    effect_model
    resource_model
    termination_model
    failure_model
}
```

Für den einfachsten Fall besitzt der Aktivierungsknoten Default-Werte:

```text
activation_node: {
    trigger_condition: on_completion_of_start_glyph
    start_conditions: validate_required_components
    activation_mode: immediate
    resource_binding: prepay_required_cost
    execution_policy: execute_once
    termination_policy: after_sequence
    cooldown_or_rearm_policy: none
    failure_policy: abort_if_invalid
}
```

Beispiel:

```text
Ziel: kleiner Stein
Wirkung: um 1 Meter nach rechts bewegen
Energiequelle: Körperenergie
Start: Start-Glyphe fertiggestellt
Ausführung: einmalig
Ende: nach abgeschlossener Bewegung
```

---

## 5. Start- und Ausführungsmodi

### 5.1 Sofortige Einmalausführung

```text
on_complete → execute_once → after_sequence
```

**Beispiel:**

```text
Erhitze diese Wasserzelle einmalig um 10 K.
```

**Eigenschaften:**

- einfachster Standardfall
- keine explizite Scharfschaltung
- kein Halten
- kein Trigger außer Fertigstellung der Start-Glyphe

---

### 5.2 Vorbereiteter, getriggerter Zauber

```text
armed → wait_for(trigger) → execute
```

**Beispiele:**

- Start bei bestimmter Vokalisierung
- Start bei bestimmter Geste
- Start bei Kontakt
- Start bei Umweltbedingung
- Start nach Zeit

**Eigenschaften:**

- Zauber kann in der Welt vorbereitet werden
- Ausführung beginnt erst bei explizit definierter Bedingung
- wichtig für Fallen, Rituale, Artefakte, Schutzkreise und Makros

---

### 5.3 Gehaltener Zauber

```text
trigger_hold → continuous_draw → stop_on_release
```

**Beispiel:**

```text
Lasse diesen Stein schweben, solange die Geste gehalten wird.
```

**Eigenschaften:**

- kontinuierlicher Mana-/Energieverbrauch
- Laufzeitinput möglich, z. B. Richtung oder Stärke
- endet bei Loslassen, Ressourcenmangel, Zielverlust oder Failsafe

---

### 5.4 Toggle-Zauber

```text
trigger_once → on
trigger_again → off
```

**Beispiele:**

- Licht an/aus
- Barriere aktivieren/deaktivieren
- Schwebemodus aktivieren/deaktivieren

**Eigenschaften:**

- bequem für Dauerfunktionen
- gefährlich ohne Dauerlimit, Quellenlimit oder Sicherheitsabschaltung

---

### 5.5 Dauerbegrenzter Zauber

```text
start → sustain_for(duration) → stop
```

**Beispiel:**

```text
Erzeuge Licht für 30 Sekunden.
```

**Eigenschaften:**

- klar begrenzter Dauerverbrauch
- wichtiges Sicherheits- und Komfortmuster
- gut für Einsteiger-Makros und Artefakte

---

### 5.6 Bedingungsgebundener Zauber

```text
while(condition) execute
until(condition) execute
```

**Beispiele:**

```text
Halte die Tür verschlossen, solange jemand im Raum ist.
```

```text
Stoppe, wenn die Temperatur über 350 K steigt.
```

**Eigenschaften:**

- verbindet Zaubersyntax mit Informationskomponenten
- braucht definierte Wahrnehmungs-, Mess- oder Zielbedingungen
- darf nicht zu allwissender Magie führen

---

### 5.7 Autonomer Quellenlauf

```text
start → autonomous_continuous_draw → until_resource_depleted
```

**Beispiel:**

```text
Erzeuge kontinuierliche Luftbewegung, bis der gebundene Kristall leer ist.
```

**Eigenschaften:**

- Zauber läuft nach Start selbstständig
- nützlich für Rituale, Maschinen, Infrastruktur und Artefakte
- gefährlich bei biologischer Quelle oder fehlender Abschaltung

**Risiko:**

```text
Zauberer als Quelle + kein Limit + vergessen = kompletter Ressourcenverbrauch
```

Dieser Modus sollte später vermutlich visuell als riskant oder unsicher erkennbar sein.

---

### 5.8 Wiederholung / Puls / Loop

```text
repeat n times
repeat every t seconds
repeat while condition
repeat until resource empty
```

**Beispiele:**

- alle 2 Sekunden ein Luftstoß
- fünf kurze Wärmepulse
- periodische Analyse eines Bereichs

**Eigenschaften:**

- erzeugt diskrete Wiederholungen statt kontinuierlicher Wirkung
- braucht Grenzen gegen Endlosschleifen und Ressourcenleerlauf

---

## 6. Abbruch und Failsafe

Abbruchlogik ist kein eigener Startmodus, aber eine notwendige Sicherheitskomponente.

```text
abort_if(condition)
```

Mögliche Abbruchgründe:

- Energiequelle reicht nicht
- Zielbindung bricht
- Ziel wird ungültig
- Fokus oder Bibliothek fehlt
- Zaubergeometrie wird beschädigt
- Temperatur, Druck oder Rückkopplung überschreitet Grenzwert
- biologische Quelle erreicht Reservegrenze
- Simulation kann Effekt nicht stabil ausführen

Failsafes können Zauber sicherer, aber teurer oder träger machen.

```text
Einsteiger-Makro = Effekt + viele Sicherheitsprüfungen + Overhead
Expertenzauber = weniger Overhead, aber riskanter oder präziser
```

---

## 7. Visuelle Implikation

Die Start-Glyphe sollte in der visuellen Sprache semantisch lesbar sein.

Mögliche visuelle Bestandteile:

| Visuelles Element | Funktion |
|---|---|
| Start-Kern | ausführbarer Einstiegspunkt |
| Trigger-Marker | Fertigstellung, Stimme, Geste, Kontakt, Zeit, Umwelt |
| Modus-Ring | einmalig, gehalten, Toggle, autonom, wiederholt |
| Ressourcen-Kopplung | Vorabkosten, Dauerverbrauch, Speicher, Quelle |
| Stop-Marker | Ende nach Sequenz, Dauer, Bedingung oder Ressourcenende |
| Sicherheitsknoten | Abbruchlogik, Grenzwerte, Rückkopplungsschutz |

Dadurch kann ein erfahrener Zauberer grob erkennen:

- Feuert der Zauber sofort?
- Wartet er auf einen Trigger?
- Läuft er autonom weiter?
- Hat er eine definierte Abschaltung?
- Zieht er kontinuierlich aus einer Quelle?
- Besitzt er Sicherheitslogik?

---

## 8. Beispiele

### Feuerball-artiger One-Shot

```text
trigger_condition: on_completion_of_start_glyph
activation_mode: immediate
resource_binding: prepay_required_cost
execution_policy: execute_once
termination_policy: after_sequence
failure_policy: abort_if_invalid_or_unpayable
```

### Schwebender Stein, gehalten

```text
trigger_condition: gesture_hold
activation_mode: held
resource_binding: continuous_draw
execution_policy: continuous_force_application
termination_policy: on_release_or_resource_failure
failure_policy: lower_or_drop_target_depending_on_safety
```

### Ritual-Lüfter mit Kristallquelle

```text
trigger_condition: manual_start
activation_mode: autonomous
resource_binding: bound_source_crystal
execution_policy: continuous_air_motion
termination_policy: until_resource_depleted_or_abort_condition
failure_policy: stop_if_overheat_or_geometry_breaks
```

---

## 9. Offene Fragen

| Kategorie | Frage |
|---|---|
| Offene Frage | Darf ein Zauber mehrere Start-Glyphen bzw. Aktivierungsknoten besitzen? |
| Offene Frage | Können mehrere Trigger gleichberechtigt denselben Zauber starten? |
| Offene Frage | Wird `until_resource_depleted` standardmäßig erlaubt oder braucht es eine explizite Unsafe-Markierung? |
| Offene Frage | Wie werden Cooldowns formal modelliert: an Zauber, Quelle, Fokusmedium oder Zauberer gebunden? |
| Offene Frage | Kann ein bereits platzierter Zauber nachträglich um Start-/Stop-Modifier ergänzt werden? |
| Offene Frage | Wie wird eine beschädigte Start-Glyphe interpretiert: ungültig, falscher Trigger, Dauerfeuer oder gar keine Kopplung? |
| Offene Frage | Wie stark muss der visuelle Editor gefährliche autonome Modi hervorheben? |

---

## 10. Arbeitsstand

| Kategorie | Inhalt |
|---|---|
| Festgelegt | Ohne Start-Modifier gilt `on_complete_execute_once`. |
| Festgelegt | Startbedingungen, Verzögerungen, Vokalisierung, Gestik und Umwelttrigger müssen explizit modelliert werden. |
| Hypothese | Jeder ausführbare Zauber besitzt genau mindestens einen Aktivierungsknoten. |
| Hypothese | Die Start-Glyphe enthält oder referenziert Trigger, Ausführungsmodus, Ressourcenbindung, Termination und Fehlerlogik. |
| Feature | Visuell unterscheidbare Start-, Trigger-, Sustain-, Toggle-, Loop- und Abort-Glyphen. |
| Beispiel | Feuerball = sofortiger One-Shot. |
| Beispiel | Schwebender Stein = gehaltener Dauerzauber. |
| Beispiel | Ritual-Lüfter = autonomer Quellenlauf. |
