# SBB Delay Analysis with Dask

## 📄 Project Overview

This project analyzes the SBB (Swiss Federal Railways) real-time delay data using **Dask**, a parallel computing library that scales efficiently with large datasets. The objective is to evaluate long-distance train punctuality and identify trends in train delays.

---

## 🗂 Dataset

- **Source**: [Open Transport Data](https://opentransportdata.swiss/de/dataset/ist-daten-sbb)
- **Files Used**: `ist-daten-2025-01.zip` through `ist-daten-2025-05.zip`
- **Volume**: Hundreds of millions of rows in total across the 5 months.

---

## ⚙️ Setup Instructions

### 1. Environment Setup

```bash
pip install -r requirements.txt
```

Make sure `dask`, `pandas`, `matplotlib`, `seaborn`, `requests`, and `pyarrow` are included.

### 2. Dask Client

Start with:

```python
from dask.distributed import Client, LocalCluster
cluster = LocalCluster()
client = Client(cluster)
```

Optional for autoscaling:
```python
client.cluster.adapt(minimum=2, maximum=8)
```

---

## 🧠 Analysis Steps

1. **Download & Extract** monthly ZIP archives (Jan–May 2025).
2. **Load into Dask DataFrame** with correct datetime conversions and type handling.
3. **Filter** only SBB-operated long-distance trains (IR, IC, ICE, EC).
4. **Compute Delays** by subtracting scheduled vs. real times.
5. **Categorize Delays**: Trains with >6 min delays marked as delayed.
6. **Visualizations**: Hourly trends, weekdays, most delayed lines/stations.
7. **Exported Parquet Files** (optional, for reuse).

---

## 📊 Key Findings

- **ICE trains** showed the highest average delays among long-distance lines.
- Delay peaks occur in the **evening hours** and vary slightly by **weekday**.
- Certain **stations** consistently rank among the most delayed.

---

## 🧪 Performance Notes

- Dask significantly improves performance over Pandas for >70M rows.
- Partitioning strategies and memory persistence are critical.
- Pre-filtering and `.persist()` helped optimize workflows.

---

## 🧾 Author Notes

This notebook was submitted as part of a non-Spark project assignment. For reproduction:
- Ensure you're connected to the internet (for downloading ZIPs).
- Use the Dask Dashboard (`client`) for performance monitoring.

If questions arise, feel free to reach out.

---

(c) 2025 – Team DaskTrain
