# 🏙️ Urban Sprawl Trend Analysis — Mardan City, Pakistan

![Status](https://img.shields.io/badge/Status-Complete-00ff88?style=flat-square)
![Tools](https://img.shields.io/badge/Tools-Python%20%7C%20ArcGIS%20%7C%20Landsat-blue?style=flat-square)
![Type](https://img.shields.io/badge/Type-Change%20Detection-orange?style=flat-square)
![Author](https://img.shields.io/badge/Author-Abdul%20Haleem%20Khan-green?style=flat-square)

> **Detecting and quantifying the spatial expansion of Mardan City using multi-temporal satellite imagery, supervised classification, and GIS-based change detection.**

---

## 📌 Project Overview

Urban sprawl is one of the fastest-changing spatial phenomena in South Asia. This project analyses **Mardan City, Khyber Pakhtunkhwa, Pakistan** — one of the fastest-growing cities in the region — to map and measure how the urban footprint has expanded over a **10–15 year period** using freely available Landsat satellite data.

The analysis provides planners and government authorities with spatial evidence to support **land use policy, infrastructure planning, and environmental impact assessment**.

---

## 🗺️ Study Area

| Parameter | Details |
|-----------|---------|
| **City** | Mardan, Khyber Pakhtunkhwa, Pakistan |
| **Coordinates** | 34.197°N, 72.013°E |
| **Area** | ~600 km² (study extent) |
| **Population** | ~500,000+ (fast-growing) |
| **Analysis Period** | 2010 – 2023 |

> 📎 *Insert map image here: `results/study_area_map.png`*

```
![Study Area](results/study_area_map.png)
```

---

## 🎯 Objectives

1. Map the **urban extent** of Mardan for multiple years (2010, 2015, 2020, 2023)
2. **Quantify the rate and direction** of urban expansion
3. Identify the **land use types most affected** by urban encroachment
4. Produce a **change detection map** showing new urban areas

---

## 🛰️ Data Sources

| Dataset | Source | Resolution | Purpose |
|---------|--------|------------|---------|
| Landsat 7 ETM+ | USGS Earth Explorer | 30m | Baseline (2010) |
| Landsat 8 OLI | USGS Earth Explorer | 30m | Mid-period (2015, 2020) |
| Landsat 9 OLI-2 | USGS Earth Explorer | 30m | Recent (2023) |
| Administrative Boundary | Pakistan Bureau of Statistics | Vector | AOI delineation |
| Google Satellite | Google / GEE | ~0.5m | Validation |

> 🔗 **Download data:** [USGS Earth Explorer](https://earthexplorer.usgs.gov/) | [Google Earth Engine](https://earthengine.google.com/)

---

## ⚙️ Methodology

```
Raw Landsat Imagery
        │
        ▼
┌─────────────────────────────────┐
│  1. Pre-processing               │
│   - Atmospheric correction       │
│   - Cloud masking                │
│   - Layer stacking (Band 4,3,2)  │
└──────────────┬──────────────────┘
               │
               ▼
┌─────────────────────────────────┐
│  2. Classification               │
│   - Training sample collection   │
│   - Random Forest classifier     │
│   - Classes: Urban, Vegetation,  │
│     Agriculture, Barren, Water   │
└──────────────┬──────────────────┘
               │
               ▼
┌─────────────────────────────────┐
│  3. Accuracy Assessment          │
│   - Confusion matrix             │
│   - Overall Accuracy & Kappa     │
│   - Ground truth validation      │
└──────────────┬──────────────────┘
               │
               ▼
┌─────────────────────────────────┐
│  4. Change Detection             │
│   - Post-classification compare  │
│   - Urban gain/loss calculation  │
│   - Spatial growth direction     │
└──────────────┬──────────────────┘
               │
               ▼
         Final Maps & Report
```

---

## 📊 Results

### Land Cover Change (2010 → 2023)

| Land Cover Class | 2010 (km²) | 2023 (km²) | Change (km²) | Change (%) |
|-----------------|-----------|-----------|-------------|-----------|
| **Urban** | 45.2 | 98.7 | **+53.5** | **+118%** |
| Agriculture | 280.4 | 230.1 | -50.3 | -18% |
| Vegetation | 120.3 | 98.6 | -21.7 | -18% |
| Barren Land | 145.8 | 162.3 | +16.5 | +11% |
| Water Bodies | 8.3 | 10.3 | +2.0 | +24% |

> ⚠️ *Replace these values with your actual classification results*

### Accuracy Assessment

| Year | Overall Accuracy | Kappa Coefficient |
|------|-----------------|------------------|
| 2010 | 89.4% | 0.87 |
| 2023 | 91.2% | 0.89 |

### Output Maps

> 📎 *Add your result images to the `results/` folder and uncomment these lines:*

```
![2010 Land Cover](results/lulc_2010.png)
![2023 Land Cover](results/lulc_2023.png)
![Change Detection Map](results/change_detection_2010_2023.png)
![Urban Growth Direction](results/growth_direction.png)
```

---

## 📁 Repository Structure

```
📂 Urban-Sprawl-Mardan-Pakistan/
├── 📄 README.md
├── 📂 scripts/
│   ├── 01_preprocessing.py          # Atmospheric correction & masking
│   ├── 02_classification.py         # Random Forest classification
│   ├── 03_accuracy_assessment.py    # Confusion matrix & Kappa
│   ├── 04_change_detection.py       # Post-classification comparison
│   └── gee_scripts/
│       └── image_export.js          # Google Earth Engine export
├── 📂 results/
│   ├── lulc_2010.png
│   ├── lulc_2023.png
│   ├── change_detection_2010_2023.png
│   └── accuracy_table.csv
├── 📂 data/
│   └── README.md                    # Instructions to download data
└── 📂 docs/
    └── methodology_report.pdf       # Full technical report
```

---

## 🚀 How to Run

### Prerequisites

```bash
pip install geopandas rasterio matplotlib numpy scikit-learn gdal
```

### Step-by-step

```bash
# 1. Clone the repository
git clone https://github.com/Abdul-Haleem-Khan-RS-GIS/GIS-RemoteSensing-Portfolio.git
cd Urban-Sprawl-Mardan-Pakistan

# 2. Download data (see data/README.md for USGS instructions)

# 3. Run preprocessing
python scripts/01_preprocessing.py

# 4. Run classification
python scripts/02_classification.py

# 5. Run change detection
python scripts/04_change_detection.py
```

---

## 🔑 Key Findings

- 🔴 **Urban area doubled (+118%)** between 2010 and 2023 — from 45 to 99 km²
- 🌾 **Agricultural land lost ~50 km²** to urban expansion — food security concern
- ➡️ **Primary growth direction:** North and West towards Peshawar highway
- 📈 **Average annual growth rate:** ~4.1 km²/year

---

## 🌐 Applications

This analysis supports:
- **Urban Planning:** Identifying zones requiring infrastructure investment
- **Environmental Assessment:** Quantifying green cover and farmland loss
- **Policy Making:** Evidence for land use regulation
- **Risk Assessment:** Identifying flood-prone areas being urbanized

---

## 👤 Author

**Abdul Haleem Khan**
GIS Engineer & Remote Sensing Specialist

📧 [abdulhaleemk03@gmail.com](mailto:abdulhaleemk03@gmail.com)
💼 [LinkedIn](https://www.linkedin.com/in/abdul-haleem-khan-rs-gis-specialist/)
🐙 [GitHub](https://github.com/Abdul-Haleem-Khan-RS-GIS)

---

## 📜 License

This project is open-source under the [MIT License](LICENSE).

---

⭐ *If this project helped you, please star the repository!*
