# BiciMAD Bike-Sharing Analytics

Large-scale analysis of Madrid's **BiciMAD** public bike-sharing system using **Apache Spark**, processing 3.8 million trips across all 12 months of 2019.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?style=flat&logo=apachespark&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logo=matplotlib&logoColor=white)

> University project — Parallel Programming course, Universidad Complutense de Madrid (May 2023). The full report is available in [`Bicimad2019.pdf`](Bicimad2019.pdf).

---

## Objective

Explore rider behaviour and station activity in Madrid's bike-sharing network by answering:

- Which **age groups** use BiciMAD the most?
- What is the **average trip duration** overall and by demographic?
- Which are the **busiest and quietest stations**?
- How does usage vary by **month and season**?

---

## Dataset

| Detail | Value |
|---|---|
| Source | [EMT Madrid Open Data](https://opendata.emtmadrid.es/) |
| Period | January – December 2019 |
| Format | 12 monthly JSON files |
| Total trips | **~3.8 million** |

### Key Fields

| Field | Description |
|---|---|
| `ageRange` | Rider age group (0 = unknown, 1 = 0–16, 2 = 17–18, 3 = 19–26, 4 = 27–40, 5 = 41–65, 6 = 66+) |
| `travel_time` | Trip duration in seconds |
| `idunplug_station` | Departure station ID |
| `idplug_station` | Arrival station ID |
| `user_type` | 0 = unknown, 1 = annual, 2 = occasional, 3 = employee |

---

## Key Findings

### Rider Demographics
- **44%** of trips have unknown age (group 0) — a data quality issue flagged for BiciMAD to improve
- Among known-age riders: **27–40 year-olds** dominate (28%), followed by **41–65** (21%)
- Youngest riders (0–16) have the **longest average trips** (~28 min), possibly because cycling is their primary transport

### Trip Duration
- Overall average trip: **~16 minutes** (990 seconds)
- Seasonal variation is minimal (~18–19 min across all seasons)

### Seasonality
| Season | Trips | Share |
|---|---|---|
| Autumn | 1,418,467 | **37%** |
| Spring | 994,221 | 26% |
| Summer | 872,388 | 23% |
| Winter | 502,608 | 13% |

- **October** is the busiest month (441K trips); **July** is the quietest (138K)
- Heat in summer and cold in winter suppress usage; mild autumn weather drives peak demand

### Station Activity
- **Station 175** is the busiest for both arrivals and departures — likely located in a high-traffic tourist or commercial area
- **Station 2008** is the least used in both directions

---

## Tech Stack

| Component | Tools |
|---|---|
| Processing | PySpark (Apache Spark) |
| Visualisation | Matplotlib |
| Language | Python |

---

## Repository Structure

```
Practica-BiciMad/
├── Practica_BiciMAD/
│   └── EstudioGeneral.py      # Main analysis: seasonality, months, stations
├── Bicimad2019.pdf             # Full project report with results and charts
├── requirements.txt            # Python dependencies
└── README.md
```

> **Note:** The raw BiciMAD JSON data files (~2 GB) are not included in the repo. They can be downloaded from [EMT Madrid Open Data](https://opendata.emtmadrid.es/).

---

## How to Run

```bash
# 1. Clone the repo
git clone https://github.com/eledelaf/Practica-BiciMad.git
cd Practica-BiciMad

# 2. Set up environment
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# 3. Download BiciMAD 2019 data
#    Place the 12 monthly JSON files in the working directory
#    (see dataset section above for the source)

# 4. Run the analysis
cd Practica_BiciMAD
spark-submit EstudioGeneral.py
```
