![Header](./images/header.png)

# PV Trainer

**PV Trainer** ist eine App für iOS &amp; iPadOS zum Planen, Simulieren und Analysieren von Photovoltaik-Anlagen (PV). Dieses Repository ist der öffentliche **Informations-Hub** der App: Es dokumentiert, was die App kann, stellt Referenzdaten bereit und ist der Ort, um **fehlende PV-Module** für die Modul-Datenbank vorzuschlagen.

> ⚠️ **Hinweis:** PV Trainer ist ein Lern- und Planungswerkzeug. Alle Ergebnisse sind **grobe Richtwerte**, die ein **Gefühl für das Verhalten** einer PV-Anlage vermitteln sollen — sie sind **keine belastbare Simulation** und **nicht verbindlich für Planungsentscheidungen**. Für echte Projekte gelten professionelle Planung und Herstellerdaten.

---

## Was die App kann

- **Bestrahlung (PVGIS):** Standort auf der Karte wählen, Neigung, Azimut und Zeitraum festlegen und Einstrahlungsdaten von **PVGIS** abrufen. Das ist die Basis aller Ertragsberechnungen.
- **Modulbibliothek:** Auswahl aus tausenden PV-Modulen aus einer Online-Datenbank. **Suche** nach Name/Hersteller und **Filter** nach Leistung (Wp) und Hersteller, plus **Favoriten**.
- **IV-Kurve:** Strom-Spannungs-Kennlinie eines Moduls bei verschiedenen Einstrahlungs-/Temperaturbedingungen, mit ablesbarem Gitternetz und der Leistung im Maximum-Power-Point (MPP). Zwei Module lassen sich direkt **gegenüberstellen**.
- **IV-Diagnose (Fluke-Stil):** Vergleich eines **gemessenen Sweeps** mit der Modellkurve zur Erkennung typischer Fehlerbilder. Sechs ladbare Vorlagen sind enthalten: *Stufen/Kerben, niedriger Isc, niedriger Voc, erhöhter Serienwiderstand (Rs), niedriger Parallelwiderstand (Rsh)* und *abgerundetes Knie*. Ausgegeben werden Befunde (mit Schweregrad), mögliche Ursachen, eine Empfehlung und Kennwerte.
- **Spezifischer Jahresertrag:** Schätzt den erwarteten Jahresertrag aus Modul, Anzahl und Wechselrichter-Wirkungsgrad — live aktualisiert.
- **Wirtschaftlichkeit:** Vergleicht deinen Verbrauch (Personen, Wärmepumpe, E-Auto, Homeoffice) mit dem PV-Ertrag. Optionaler **Speicher** und pflegbare **Tarife** (Strompreis &amp; Einspeisevergütung). Ergebnisse: Eigenverbrauch, Autarkie, Ersparnis und **vermiedenes CO₂** — mit Grafiken und Jahresverlauf. Die Berechnung läuft **auf dem Gerät** über eine Stunden-Simulation mit typischen Lastprofilen.
- **Ertragsanalyse:** Bewertet die Abweichung zwischen gemessenem und modelliertem Ertrag (RMSE, MBE, MAE, nRMSE, R²), mit Residuen und Fehler nach Einstrahlung.
- **PV Trainer Pro:** Einige erweiterte Funktionen sind über das optionale **PV-Trainer-Pro**-Abo verfügbar.

Datenquellen sind direkt integriert: **PVGIS** (Einstrahlung), **SMARD** (Strommarktdaten) und die PV-Trainer-Modul-Datenbank.

---

## Fehlendes Modul vorschlagen

Fehlt ein Modul in der Datenbank, kannst du es vorschlagen. **Es genügen die Datenblattwerte** — die CEC-Single-Diode-Parameter werden automatisch auf dem Server berechnet.

**Zwei Wege:**

1. **In der App (am einfachsten):** `Einstellungen → Beitragen → Fehlendes Modul melden`. Öffnet eine vorausgefüllte E-Mail an `info@pv-trainer.de` im Format unten.
2. **GitHub-Issue:** Neues Issue in diesem Repository über die Vorlage **„Modul-Vorschlag"**.

### Benötigte Datenblattwerte

| Feld | Beschreibung |
| --- | --- |
| `name` | Modulname (eindeutig, wie er erscheinen soll) |
| `manufacturer` | Herstellername |
| `celltype` | Einer von: `monoSi`, `multiSi`, `polySi`, `cis`, `cigs`, `cdte`, `amorphous` |
| `V_mp` | Spannung im MPP [V] |
| `I_mp` | Strom im MPP [A] |
| `V_oc` | Leerlaufspannung [V] |
| `I_sc` | Kurzschlussstrom [A] |
| `alpha_sc` | Temperaturkoeffizient von I_sc [A/°C] — falls Datenblatt %/°C: `%/100 × I_sc` |
| `beta_voc` | Temperaturkoeffizient von V_oc [V/°C] — meist negativ; falls %/°C: `%/100 × V_oc` |
| `gamma_pmp` | Temperaturkoeffizient von P_max [%/°C] — meist negativ |
| `cells_in_series` | Anzahl der Zellen in Reihe |
| `source` | Datenblatt-Link (optional) |

Bitte stelle sicher, dass alle Werte aus einer verlässlichen Quelle stammen (z. B. dem Hersteller-Datenblatt). Einreichungen werden vor der Aufnahme manuell geprüft.

---

## Erlaubte Zelltypen

Der Zelltyp definiert die PV-Technologie und muss einem der erlaubten Werte entsprechen. Viele gängige Namen werden automatisch erkannt:

```ruby
ALLOWED_CELLTYPES = ["monoSi", "multiSi", "polySi", "cis", "cigs", "cdte", "amorphous"]

TECHNOLOGY_MAPPING = {
    # Monokristallines Silizium
    "Mono-c-Si": "monoSi",
    "Mono-cSi": "monoSi",
    "Monocrystalline Silicon": "monoSi",
    "Mono-Si": "monoSi",
    "Mono c-Si": "monoSi",
    "Monocrystalline": "monoSi",
    "Mono-crystalline": "monoSi",
    # Multikristallines Silizium
    "Multi-c-Si": "multiSi",
    "Multi-cSi": "multiSi",
    "Multicrystalline Silicon": "multiSi",
    "Multi-Si": "multiSi",
    "Multi c-Si": "multiSi",
    "Multicrystalline": "multiSi",
    "Multi-crystalline": "multiSi",
    # Polykristallines Silizium
    "Poly-c-Si": "polySi",
    "Poly-cSi": "polySi",
    "Polycrystalline Silicon": "polySi",
    "Poly-Si": "polySi",
    "Poly c-Si": "polySi",
    "Polycrystalline": "polySi",
    "Poly-crystalline": "polySi",
    # Amorphes Silizium
    "Amorphous Silicon": "amorphous",
    "a-Si": "amorphous",
    "Amorphous": "amorphous",
    "Amorphous Silicon (a-Si)": "amorphous",
    # Cadmiumtellurid
    "CdTe": "cdte",
    "Cadmium Telluride": "cdte",
    "Cadmium-Telluride": "cdte",
    # Kupfer-Indium-Diselenid
    "CIS": "cis",
    "Copper Indium Diselenide": "cis",
    "Copper-Indium-Diselenide": "cis",
    # Kupfer-Indium-Gallium-Diselenid
    "CIGS": "cigs",
    "Copper Indium Gallium Diselenide": "cigs",
    "Copper-Indium-Gallium-Diselenide": "cigs",
    # Weitere Technologien
    "HIT": "monoSi",          # HIT-Zellen sind monokristallines Si mit dünner amorpher Schicht
    "Heterojunction": "monoSi",
    "Perovskite": "amorphous", # kein exaktes Äquivalent, angenähert
    "DSC": "amorphous",        # farbstoffsensibilisierte Zellen als amorph behandelt
}
```

---

## Datenquellen

- **PVGIS** – Photovoltaic Geographical Information System, © Europäische Union, Joint Research Centre (JRC)
  <https://joint-research-centre.ec.europa.eu/photovoltaic-geographical-information-system-pvgis_en>
- **SMARD** – Strommarktdaten, © Bundesnetzagentur
  <https://www.smard.de/home/downloadcenter/download-marktdaten/>
- **NREL SAM** – Modulparameter basieren teils auf der CEC-Modul-Datenbank des NREL System Advisor Model (SAM).

---

## Fehler melden

Fehler in den Moduldaten gefunden oder einen Vorschlag? Bitte ein GitHub-Issue in diesem Repository erstellen. Meldungen werden geprüft und bei Bedarf korrigiert.

## Mitwirken

Beiträge von allen, die sich für Solarenergie begeistern, sind willkommen. Danke, dass du PV Trainer verbesserst und Solarenergie unterstützt! ☀️
