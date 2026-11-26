# Bike-Sharing Demand Analysis and Prediction – SECSE001 Capstone

**Student:** Subham Tewatia  **Roll No:** 2601940017  **Programme:** MCA (AI/ML), Semester I
**Course:** Data Analysis with Power BI & KNIME (SECSE001)  **Faculty:** Jyoti Yadav
**University:** K.R. Mangalam University, Gurugram

## Dataset
Bike Sharing Dataset (Capital Bikeshare, Washington D.C., 2011–2012), UCI Machine Learning Repository:
https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset
Raw files are in `raw_data/` (`day.csv`, `hour.csv`, `Readme.txt`).

## Tools
- Power BI (Power Query, DAX, report with forecast, Key influencers and drill-through)
- KNIME Analytics Platform 5.12 (cleaning component, EDA, Decision Tree, k-Means)

## Files
| File | Contents |
|---|---|
| `2601940017_Capstone.pbix` | Power BI report: 4 tables, 7 DAX measures, 4 pages (Overview, Trends & Forecast, ML Insights, Season Detail drill-through) |
| `2601940017_Capstone.knwf` | KNIME workflow: cleaning component, statistics, correlation, charts, Decision Tree, k-Means, CSV/Excel export |
| `Cleaned_Data.csv` | Final cleaned dataset (731 days × 20 columns) |
| `Predictions.csv` | Decision Tree predictions on the 220 test days |
| `Clusters.csv` | Each day with its k-Means cluster and cluster name |
| `EDA_Report.xlsx` | Statistics, correlation, model accuracy and cluster profile from KNIME |
| `2601940017_Capstone_Report.pdf` | Project report |
| `screenshots/` | Screenshots used in the report |
| `raw_data/` | Original UCI files |

## How to open
- **Power BI:** open `2601940017_Capstone.pbix` in Power BI Desktop (or upload it to the Power BI service). Use the slicers on the Overview page; right-click a season and choose *Drill through → Season Detail*.
- **KNIME:** File → Import KNIME Workflow → select `2601940017_Capstone.knwf`. Then right-click the workflow → Reset all, and Execute all. Output files are written next to the workflow data folder.
- **CSV / Excel files:** open in Excel or any text editor.
- **Report:** open `2601940017_Capstone_Report.pdf` in any PDF reader.
