# Power BI Case Study: Bearbus Workshop Warehouse Material Flow Optimization

## Profile and Core Competencies / Kompetenzprofil

### English Summary
* Project Goal: Analyzed 258K transactional logistics records to eliminate material outbound delays, optimize high-frequency warehouse slots, and uncover picking accuracy anomalies at the Bearbus assembly plant.
* Technical Skills Applied: Power Query ETL, Time-Intelligence Parsing, Advanced DAX Measure Engineering, Relational Data Modeling, and Statistical Outlier Diagnostics (Scatter Plots, Distribution Histograms).
* Business Value: Optimized 5 critical warehouse storage configurations, isolated a major 190+ hour process bottleneck, solved weekend scheduling backlogs, and replaced manual data processing days with interactive reporting hours.

### Deutsche Zusammenfassung
* Projektziel: Analyse von 258K Logistiktransaktionen zur Beseitigung von Materialausgangsverzögerungen, Optimierung von Hochfrequenz-Lagerplätzen und Erkennung von Kommissionierfehlern im Bearbus-Montagewerk.
* Angewandte Hard Skills: Power Query ETL, Zeitreihenanalysen, fortgeschrittene DAX-Formeln, relationale Datenmodellierung und statistische Ausreißerdiagnostik (Punktdiagramme, Verteilungshistogramme).
* Geschäftlicher Nutzen: Datenbasierte Optimierung von 5 Lagerplätzen, Isolierung eines 190+-stündigen Prozessengpasses, Aufklärung von Wochenend-Rückstaus und Reduzierung der Analysezeit von Tagen auf interaktive Stunden.

---

## Project Assets and Management Report

To review the visual charts, interactive design choices, and full dashboard pages constructed for this business intelligence operation, access the document below:

* 👉 **[View the Full PDF Dashboard](Project1_Lagerlogistik_en.pdf)**

---

## 1. Project Overview and Operational Scenario
The manufacturing group Bearbus operates an aerospace assembly facility at the Melli-Beese plant. The assembly floor relies on a localized workshop warehouse (Werkstattlager) where individual components are temporarily stored before moving into final production. Facing logistical friction and slow material access, the enterprise required an analytical framework to monitor the warehouse software system's historical data export.

As the Data Analyst, my mandate was to process 258,000 transaction records (TA-Nummer) to solve a critical operational question: When and where are unusual delays recorded during material checkouts (Materialausgang)? The ultimate business objective was to minimize material outbound delays, optimize 5 high-frequency warehouse storage slots, and systematically improve manual picking accuracy.

## 2. Technical Stack and Competency Matrix
* Business Intelligence Tool: Power BI Desktop
* Data Processing (ETL): Power Query (Excel flat file ETL, raw data transformations, and Kalenderwoche calendar week feature engineering).
* Calculation Engine: Data Analysis Expressions (DAX metrics tracking TA-Nummer aggregation, Bearbeitungszeit time-deltas, and dynamic material averages).
* Relational Modeling: Multi-table schema design linking transactional log ledgers directly to structural material data description tables.
* Analytical Visualizations Created: 
  1. Line Chart: TA-Nummer tracking velocity trends by calendar week.
  2. Histogram: Processing duration (Bearbeitungszeit) distribution curves.
  3. Bar Chart: Average processing turnaround times grouped by material type.
  4. Line Chart: Material movement frequency to establish slot rankings.
  5. Scatter Plot: Sollmenge Von vs. Sollmenge Nach quantity deviation mapping.
  6. Bar Chart: Average processing times broken down by specific weekdays.

---

## 3. Key Metrics Discovered
* Total Transactions Audited: 258,000 unique TA-Nummern
* Weekly Workload Velocity Average: 9,586 TA-Nummern
* Weekly Workload Velocity Median: 10,919 TA-Nummern
* Prime System Bottleneck Identified: Deckplatte DPL 2-W3 (190+ hour average turnaround delay across 177 distinct movements)

---

## 4. Root Cause Diagnostics and Analytics Insights

### Transaction Volume and Workload Trends
Analyzing temporal patterns via line charts by creation week (Erst.Woche) revealed severe operational workload volatility. The statistical variance between the weekly median (10,919) and the weekly average (9,586) proved that warehouse teams face massive, sharp demand peaks rather than a steady stream of items, causing temporary operational stress on floor personnel.

### Chronological Processing and Weekend Backlog Patterns
The processing duration (Bearbeitungszeit) was calculated by mapping the time-delta between creation timestamps (Erst.Datum/Zeit) and outbound goods issue timestamps (Ausgang.Datum/Zeit). A distribution histogram revealed that while most standard checkouts clear efficiently within a 0–32 hour window, severe secondary peaks emerge between 32–95 hours and 127–158 hours. 

Cross-referencing this timeline delay with weekdays exposed a clear Weekend Backlog Pattern: orders initiated on Sundays regularly sit idle, leading to heavy processing bottlenecks when the Monday morning shift arrives. Additionally, an extreme systemic anomaly was caught during low-volume operations in June, where processing times spiked to a 307-hour peak, pointing to an unmanaged operational factory shutdown.

### Warehouse Storage Slot Optimization
To accelerate material retrieval speeds, a line chart analysis mapped out item movement frequencies to rank parts. The top 3 components generating the heaviest overall transaction velocity were isolated:
1. Dichtungen (Seals)
2. Hebel (Levers)
3. Zugfedern (Tension Springs)

Strategic Outcome: These 3 high-volume item classes were moved out of background storage and assigned directly to prime exit warehouse slots to speed up retrieval. Conversely, slower components like Distanzbolzen and Stützscheiben were re-allocated to deep, central storage slots since they are rarely accessed.

### Picking Accuracy and Quality Safeguards
A scatter plot was constructed to map out ordered source quantities versus final moved quantities (Sollmenge Von vs. Sollmenge Nach). In a flawless picking environment, all records line up perfectly along a 45-degree diagonal line. The visual grid instantly flagged 3 critical outlier transactions falling far below the diagonal line, meaning the physical quantity moved out of the warehouse was lower than what production had ordered. These explicit gaps were flagged and sent to the operations team for a targeted quality audit.

### Critical Process Bottlenecks
A comparative evaluation of material categories revealed a massive operational bottleneck: the cover plate component Deckplatte DPL 2-W3 recorded an extreme average processing delay of over 190+ hours across 177 distinct movements. This long delay stands out as a clear systemic bottleneck, and the data was sent to management to launch an immediate process audit.

---

## 5. Documented Business Value and Project Impact
* Optimized 5 major warehouse storage layouts by replacing old placement habits with data-driven frequency analytics, accelerating active material checkout speeds.
* Solved the facility's weekend processing mystery by proving that Sunday orders cause heavy Monday backlogs, enabling management to adjust staff shifting schedules.
* Identified the organization's #1 process bottleneck (Deckplatte DPL 2-W3, averaging 190+ hours), giving process engineers the exact target needed to fix workflow friction.
* Discovered 3 critical manual picking discrepancies, enabling the quality management team to set up localized data validation checks.
* Streamlined corporate reporting velocity, replacing days of slow manual Excel data processing with an automated, interactive Power BI tracking dashboard.

---

