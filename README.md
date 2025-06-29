# Projekt: Analyse von SBB-Verspätungen mit Dask (Mai 2025)

## Projektübersicht

In diesem Projekt analysieren wir die effektiven Verspätungsdaten der SBB-Fernverkehrszüge im Monat **Mai 2025**. Ziel ist es, Muster zu erkennen: 
- Welche Linien sind besonders oft verspätet?
- An welchen Wochentagen oder zu welchen Uhrzeiten treten Verspätungen vermehrt auf?
- Welche Bahnhöfe sind am häufigsten von verspäteten Fahrten betroffen?

Für die Datenverarbeitung wurde **Dask** verwendet – ein verteiltes Python-Framework für die Analyse großer Datenmengen.

---

## Technische Umsetzung

- **Datenquelle:** Open Transport Data Schweiz  
  `https://archive.opentransportdata.swiss/istdaten/2025/ist-daten-2025-05.zip`
- **Dateiformat:** CSV-Dateien (gezippt)
- **Größe nach Entpacken:** ~2 GB (über 70 Millionen Zeilen)
- **Verarbeitungsschritte:**
  - Laden und Parsen der CSV-Dateien mit Dask
  - Konvertieren von Datumsfeldern
  - Filtern auf SBB und Fernverkehr (`IC`, `IR`, `ICE`, `EC`)
  - Berechnung von Verspätungen in Minuten
  - Erkennen von „verspätet“ ab >6 Minuten
  - Gruppierungen und Visualisierungen

---

## Voraussetzungen

- Python ≥ 3.10
- Installation der benötigten Pakete:
  ```bash
  pip install -r requirements.txt
  ```

---

## Ausführung

1. Starte Jupyter:
   ```bash
   jupyter notebook
   ```

2. Öffne das Notebook `SBB_Delays_dask.ipynb`

3. Folge den Ausführungszellen:
   - Herunterladen & Entpacken des Mai-Archivs
   - Laden ins Dask DataFrame
   - Datenbereinigung & Analyse
   - Visualisierung der Ergebnisse

---
