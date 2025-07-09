# Dynamic-Pricing-of-Parking-lots-project

This project builds a real-time pricing engine for 14 urban parking lots using historical data and live simulation. The system adjusts parking prices dynamically based on occupancy, queue length, traffic conditions, vehicle types, special days, and competitor pricing, enabling smarter resource allocation in urban settings.

---

##  Tech Stack

- **Python**
- **Pandas** – data manipulation
- **Pathway** – real-time data stream processing
- **Bokeh + Panel** – interactive visualizations
- **Mermaid** – architecture diagram
- **CSV** – intermediate and final data storage

---

##  Architecture Diagram
![flow chart](https://github.com/user-attachments/assets/944a3717-5344-4c5a-87c9-2bed4972eabf)


---
##  Architecture Explanation & Workflow

###  Preprocessing

- `dataset.csv` is converted to a time-ordered streamable dataset `parking_stream.csv`.
- A `Timestamp` column is created using `LastUpdatedDate` and `LastUpdatedTime`.

###  Streaming Simulation

- `Pathway replay_csv()` replays the stream at a specified rate.
- Additional features such as day and timestamp parsing are added.

---

## Model 1 – Baseline Pricing

- Uses only occupancy and capacity.
- Calculates the average occupancy per day.

**Formula:**
 = BASE_PRICE + ALPHA * (occupancy / capacity)


---

##  Model 2 – Demand-Based Pricing

**Incorporates:**

- Occupancy
- Queue Length
- Traffic Conditions
- Special Day Indicator
- Vehicle Weight

All components are normalized and contribute to a **demand score**.

**Final price formula:**
 = BASE_PRICE * (1 + LAMBDA * normalized_demand)


---

##  Result Generation

- Both models export results as CSV:
  - `price_daily_per_lot.csv`
  - `baseline_model.csv`

---

##  Visualization

- **Bokeh + Panel** is used to generate interactive plots.
- **Competitor vs Model comparison** is shown for each parking lot.

