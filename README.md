# Bearbus Workshop Warehouse — Power BI Dashboard

Logistics analysis | Power BI | DAX | Power Query | 258,000 transactions

---

This project analyzes warehouse transaction data from the Bearbus aerospace assembly plant. The warehouse (Werkstattlager) stores components temporarily before they move to the assembly floor. The core question: where and when do material checkouts slow down, and what can be done about it?

The full dashboard with charts and visuals is in the PDF linked below.

**[View the Dashboard PDF](Project1_Lagerlogistik_en.pdf)**

---

## Technical Stack

| Layer | Tool / Method |
|---|---|
| BI Tool | Power BI Desktop |
| ETL | Power Query — flat file ingestion, data cleaning, calendar week engineering |
| Calculations | DAX — transaction counts, time-delta measures, dynamic averages |
| Data Model | Multi-table relational schema: transaction log linked to material description tables |

---

## Dataset

- 258,000 transaction records (TA-Nummern)
- Each record tracks: material type, storage slot, creation timestamp, outbound timestamp, ordered quantity, moved quantity
- Date range covers two years including a seasonal factory shutdown period

---

## Dashboards Built

| Page | Chart Type | What It Answers |
|---|---|---|
| Transaction velocity | Line chart by calendar week | When does workload spike? |
| Processing duration | Histogram | How long do checkouts actually take? |
| Material processing times | Bar chart by material type | Which materials cause delays? |
| Slot frequency ranking | Line chart | Which items move most often? |
| Picking accuracy | Scatter plot (Sollmenge Von vs. Nach) | Are quantities matching what was ordered? |
| Weekday breakdown | Bar chart | Which days cause backlogs? |

---

## Key Findings

### Workload is not steady — it spikes

Weekly transaction volume averaged 9,586 but had a median of 10,919. The gap between mean and median indicates the distribution is left-skewed by low-volume weeks pulling the average down. In practice, warehouse staff regularly face sharp demand peaks rather than a predictable daily flow.

### Most checkouts are fast — but a secondary cluster is not

The processing time histogram shows a clean primary cluster between 0 and 32 hours. However, two secondary peaks appear at 32–95 hours and 127–158 hours. These are not random — they follow a pattern tied to the day orders were created.

### Sunday orders cause Monday backlogs

Cross-referencing processing times with the day of the week showed that orders created on Sundays consistently idle until Monday morning. The weekday bar chart makes this visible: Monday shows disproportionately long average processing times relative to mid-week.

An additional spike to 307 hours was identified in June — traced to an unmanaged factory shutdown where no handover process was in place for open orders.

### Five warehouse slots were reorganised based on movement frequency

The slot frequency analysis ranked all materials by how often they were moved. The top three:

1. Dichtungen (Seals)
2. Hebel (Levers)
3. Zugfedern (Tension Springs)

These were relocated to prime exit slots closest to the assembly floor. Slower-moving components — Distanzbolzen and Stützscheiben — were moved to deeper central storage where access time matters less.

### One component is responsible for a 190-hour bottleneck

Comparing average processing times by material category isolated a single outlier: **Deckplatte DPL 2-W3**, averaging over 190 hours per movement across 177 recorded transactions. Every other material category cleared in a fraction of that time. This was flagged and escalated to the process engineering team.

### Three picking discrepancies flagged via scatter plot

In a clean warehouse operation, a scatter plot of ordered quantity (Sollmenge Von) against moved quantity (Sollmenge Nach) should produce a straight diagonal line — every order matched exactly. Three transactions fell clearly off that diagonal, meaning the physical quantity sent to production was lower than what was requested. These were isolated and sent to quality management.

---

## DAX Measures

```
// Weekly transaction count
TA Count = COUNTROWS('transactions')

// Processing time in hours
Bearbeitungszeit (h) =
DATEDIFF(
    MIN('transactions'[Erst.Datum/Zeit]),
    MIN('transactions'[Ausgang.Datum/Zeit]),
    HOUR
)

// Average processing time per material
Avg Processing Time =
AVERAGEX(
    VALUES('transactions'[Material]),
    [Bearbeitungszeit (h)]
)
```

---

## Project Impact

| Finding | Action Taken |
|---|---|
| 3 high-frequency materials in slow slots | Relocated to prime exit positions |
| 2 low-frequency materials in prime slots | Moved to deep central storage |
| Sunday → Monday backlog pattern | Shift scheduling adjusted |
| Deckplatte DPL 2-W3 at 190+ hours | Escalated to process engineering |
| 3 picking discrepancies | Sent to quality management for audit |
| Manual Excel reporting process | Replaced with live Power BI dashboard |

---

Dataset: Internal warehouse transaction export from Bearbus Melli-Beese assembly plant. Used for training purposes.
