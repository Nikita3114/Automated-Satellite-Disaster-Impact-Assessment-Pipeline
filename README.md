# Automated-Satellite-Disaster-Impact-Assessment-Pipeline
An end-to-end geospatial pipeline designed to automate the detection of environmental damage (Burn Scars/Vegetation Loss) using temporal satellite imagery.

## 📝 Project Overview
This project solves a critical problem in **Agritech** and **Insurtech**: verifying land damage without field visits. By ingesting raw **Landsat 8** data, the pipeline performs spectral analysis to detect changes in vegetation health before and after a disaster event.

*   **Case Study:** The Cold Springs Fire (Colorado).
*   **Technique:** Multi-temporal NDVI (Normalized Difference Vegetation Index) differencing.
*   **Outcome:** Successfully mapped the exact burn scar boundary for risk assessment.

## 🛠️ Tech Stack
*   **Language:** Python 3.12
*   **Geospatial Library:** Rasterio (for raster processing and I/O)
*   **Data Processing:** NumPy (for high-performance array math)
*   **Visualization:** Matplotlib (for generating impact heatmaps)
*   **Data Source:** Landsat 8 (via Figshare API)

## 📊 Results
The pipeline visualizes the "Before" state (Healthy), "After" state (Burnt), and the calculated **Change Detection Map**.

![Result Heatmap](result_heatmap.png)
*(Purple areas indicate severe vegetation loss due to fire)*

## 🚀 How It Works
1.  **Automated Ingestion:** The script checks for local data; if missing, it downloads and extracts the raw satellite bands via HTTP requests.
2.  **Dynamic Filtering:** Uses `glob` recursive search to identify Red (Band 4) and NIR (Band 5) files regardless of directory structure.
3.  **Spectral Analysis:** Calculates NDVI for both timeframes:
    *   `NDVI = (NIR - Red) / (NIR + Red)`
4.  **Change Detection:** Performs pixel-wise subtraction (`Post_Event - Pre_Event`) to quantify loss.

## 💻 Usage
1. Clone the repository.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
