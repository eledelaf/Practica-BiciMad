# Practica-BiciMad
This assignment designs and implements a scalable data-analysis solution using Apache Spark for large-scale storage, processing, and analytics.
We analyze the official BiciMAD bike-sharing dataset from the Madrid City Council for the full year 2019 (all 12 months). The study explores rider behavior and station activity, including:
Which age groups use BiciMAD the most
Average trip duration overall and by age group
The busiest stations
Monthly and station-level usage patterns
Repository Structure
EstudioGeneral.py — Station- and month-focused analysis (temporal patterns and station activity).
EstudioGrupoEdad.py — Annual aggregates by age group (who rides most, and for how long).
The two scripts share a common approach but differ in their focus: the first centers on stations and months, while the second summarizes annual results by age cohort.
