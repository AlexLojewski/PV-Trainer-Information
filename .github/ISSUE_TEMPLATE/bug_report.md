---
name: Bug report
about: Create a report to help us improve
title: ''
labels: ''
assignees: ''

---

name: "Modul-Vorschlag (fehlendes PV-Modul)"
description: "Ein fehlendes Modul zur Aufnahme in die DB vorschlagen. Werte vom Datenblatt genügen."
title: "[Modul] <Hersteller Modellname>"
labels: ["modul-vorschlag"]
body:
  - type: markdown
    attributes:
      value: |
        Danke für den Vorschlag! Trag die Datenblatt-Werte ein — daraus werden die
        CEC-Single-Diode-Parameter berechnet (`fit_cec_sam`). Die Freigabe erfolgt
        manuell durch den Maintainer via `python -m app.modules.add_module`.
  - type: input
    id: name
    attributes:
      label: "Modulname (name)"
      description: "Eindeutiger Name, so wie er in der DB erscheinen soll."
      placeholder: "Musterhersteller MH-450"
    validations:
      required: true
  - type: input
    id: manufacturer
    attributes:
      label: "Hersteller (manufacturer)"
      placeholder: "Musterhersteller"
    validations:
      required: true
  - type: dropdown
    id: celltype
    attributes:
      label: "Zelltyp (celltype)"
      options: ["monoSi", "multiSi", "polySi", "cis", "cigs", "cdte", "amorphous"]
    validations:
      required: true
  - type: input
    id: v_mp
    attributes:
      label: "V_mp — Spannung im MPP (V)"
      placeholder: "34.5"
    validations:
      required: true
  - type: input
    id: i_mp
    attributes:
      label: "I_mp — Strom im MPP (A)"
      placeholder: "13.05"
    validations:
      required: true
  - type: input
    id: v_oc
    attributes:
      label: "V_oc — Leerlaufspannung (V)"
      placeholder: "41.2"
    validations:
      required: true
  - type: input
    id: i_sc
    attributes:
      label: "I_sc — Kurzschlussstrom (A)"
      placeholder: "13.85"
    validations:
      required: true
  - type: input
    id: alpha_sc
    attributes:
      label: "alpha_sc — Temp.-Koeff. I_sc (A/°C)"
      description: "Absolut in A/°C. Falls das Datenblatt %/°C angibt: %/100 × I_sc."
      placeholder: "0.0055"
    validations:
      required: true
  - type: input
    id: beta_voc
    attributes:
      label: "beta_voc — Temp.-Koeff. V_oc (V/°C)"
      description: "Meist negativ. Falls %/°C: %/100 × V_oc."
      placeholder: "-0.115"
    validations:
      required: true
  - type: input
    id: gamma_pmp
    attributes:
      label: "gamma_pmp — Temp.-Koeff. P_max (%/°C)"
      description: "In %/°C, meist negativ."
      placeholder: "-0.34"
    validations:
      required: true
  - type: input
    id: cells_in_series
    attributes:
      label: "cells_in_series — Zellen in Reihe"
      placeholder: "144"
    validations:
      required: true
  - type: textarea
    id: source
    attributes:
      label: "Quelle / Datenblatt-Link (optional)"
      placeholder: "https://…/datenblatt.pdf"
    validations:
      required: false
