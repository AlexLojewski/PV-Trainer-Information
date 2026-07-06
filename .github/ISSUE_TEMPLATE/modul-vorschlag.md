---
name: Modul-Vorschlag (fehlendes PV-Modul)
about: Ein fehlendes Modul zur Aufnahme in die DB vorschlagen. Datenblatt-Werte genügen.
title: "[Modul] Hersteller Modellname"
labels: modul-vorschlag
assignees: ''
---

Danke für den Vorschlag! Bitte die Werte vom **Datenblatt** eintragen (die Zeile
mit dem Wert hinter dem Doppelpunkt ausfüllen). Daraus werden die CEC-Single-Diode-
Parameter berechnet. Freigabe erfolgt manuell durch den Maintainer.

## Modul

- **Modulname (name):**
- **Hersteller (manufacturer):**
- **Zelltyp (celltype):** <!-- einer von: monoSi, multiSi, polySi, cis, cigs, cdte, amorphous -->

## Datenblatt-Werte (STC)

- **V_mp — Spannung im MPP (V):**
- **I_mp — Strom im MPP (A):**
- **V_oc — Leerlaufspannung (V):**
- **I_sc — Kurzschlussstrom (A):**
- **cells_in_series — Zellen in Reihe:**

## Temperatur-Koeffizienten

- **alpha_sc — Temp.-Koeff. I_sc (A/°C):** <!-- falls Datenblatt %/°C: (%/100) × I_sc -->
- **beta_voc — Temp.-Koeff. V_oc (V/°C):** <!-- meist negativ; falls %/°C: (%/100) × V_oc -->
- **gamma_pmp — Temp.-Koeff. P_max (%/°C):** <!-- meist negativ -->

## Quelle (optional)

- **Datenblatt-Link / Quelle:**
