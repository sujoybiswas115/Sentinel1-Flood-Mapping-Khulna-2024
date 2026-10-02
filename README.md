# Sentinel-1 Based Flood Mapping and District-wise Inundation Assessment of Khulna Division, Bangladesh (2024)

> **GIS & Remote Sensing Project | Sentinel-1 SAR | QGIS | Flood Inundation Analysis | District-wise Zonal Statistics**

## Project Overview

This project presents a GIS- and remote-sensing-based flood mapping and district-level inundation assessment for **Khulna Division, Bangladesh**, using a binary **Sentinel-1 SAR-derived flood extent raster** for 2024.

The analysis focuses on identifying the spatial distribution of flooded areas, quantifying flood-affected area for each district, calculating district-wise flood percentage, and producing publication-quality maps, charts, and summary tables.

The workflow was completed mainly in **QGIS**, with the flood raster reprojected to a projected coordinate system for reliable area calculation.

---

## Abstract

Flooding is one of the most recurrent hydro-meteorological hazards affecting southwestern Bangladesh, where low-lying terrain, dense river networks, tidal influence, and seasonal rainfall interact to produce spatially variable inundation patterns. This study presents a Geographic Information System (GIS) and Sentinel-1 Synthetic Aperture Radar (SAR)-based assessment of flood extent across Khulna Division, Bangladesh, for 2024. A binary flood-extent raster was clipped to the administrative boundary of Khulna Division, reprojected to WGS 84 / UTM Zone 45N (EPSG:32645), and analysed at 30 m spatial resolution. District-level flood statistics were derived using zonal statistics for the 10 districts of the division. Flooded area was calculated from the number of inundated pixels, where each 30 m × 30 m pixel represented 900 m² (0.0009 km²). The analysis identified approximately 127.82 km² of flooded area within a total mapped divisional area of 20,749.63 km², corresponding to approximately 0.62% of the study area. Satkhira recorded the largest absolute flooded area (37.92 km²), followed by Khulna (36.73 km²) and Bagerhat (22.50 km²). In contrast, Narail showed the highest proportional inundation (1.134%), followed by Satkhira (1.119%) and Khulna (1.013%). The results demonstrate the value of combining Sentinel-1-derived flood information with GIS-based district-level spatial analysis for rapid flood assessment and comparative exposure mapping.

**Keywords:** Sentinel-1 SAR; flood mapping; inundation assessment; QGIS; zonal statistics; remote sensing; Khulna Division; Bangladesh

---

## 1. Introduction

Flood mapping is an essential component of disaster-risk assessment, emergency response, water-resources planning, and post-event impact analysis. In Bangladesh, flood monitoring is particularly important because of the country's deltaic setting, extensive river network, monsoonal climate, low-lying floodplains, and strong interaction between riverine, coastal, and tidal processes.

Optical satellite imagery can be limited during flood events because cloud cover frequently obscures the Earth's surface. Synthetic Aperture Radar (SAR), in contrast, can acquire information under cloudy conditions and during both day and night. Sentinel-1 SAR therefore provides an important data source for detecting and mapping surface-water and flood-related changes.

This project focuses on Khulna Division in southwestern Bangladesh. The objective was not only to map the spatial distribution of the 2024 flood extent, but also to quantify inundation at the district level. The workflow integrates a Sentinel-1-derived binary flood raster with administrative boundaries in QGIS and produces district-wise estimates of flooded area and flooded percentage. The final outputs include thematic maps, quantitative tables, comparison charts, and a reproducible GIS project structure.

---

## 2. Objectives

The main objectives of this study were to:

1. delineate the 2024 flood extent within Khulna Division;
2. prepare a clean administrative study-area boundary for the division;
3. calculate the total mapped flood-affected area in square kilometres;
4. quantify district-wise flooded area for all 10 districts of Khulna Division;
5. estimate the proportion of each district affected by flooding;
6. compare absolute flooded area and proportional inundation among districts;
7. generate publication-quality maps, charts, and summary tables; and
8. document a reproducible GIS workflow for future flood-mapping studies.

---

## 3. Study Area

Khulna Division is located in southwestern Bangladesh and contains 10 districts:

- Bagerhat
- Chuadanga
- Jessore
- Jhenaidah
- Khulna
- Kushtia
- Magura
- Meherpur
- Narail
- Satkhira

The mapped administrative area used in this project was approximately **20,749.63 km²**. The southern part of the division is characterized by a complex coastal and riverine landscape, while the northern districts are comparatively inland. This spatial variability makes district-level flood assessment useful because total flooded area and proportional inundation can differ substantially among districts.

### Study Area Map

![Study Area Map](02_Final_Maps/Map_01_Study_Area_Khulna.png)

---

## 4. Data and Software

### 4.1 Datasets

| Dataset | Purpose |
|---|---|
| Sentinel-1 SAR-derived binary flood extent raster (2024) | Flood extent mapping and area estimation |
| Bangladesh administrative district boundary data | Selection of Khulna Division districts and spatial zoning |
| Derived Khulna Division boundary | Clipping and study-area masking |
| Derived district-level flood statistics layer | District-wise quantitative analysis |

### 4.2 Software and Tools

The analysis was conducted primarily in **QGIS**, using the following GIS operations and processing tools:

- attribute-based feature selection;
- vector export;
- dissolve;
- raster clipping by mask layer;
- raster reprojection;
- nearest-neighbour resampling;
- vector reprojection;
- field calculator;
- raster unique values report;
- zonal statistics;
- graduated symbology;
- print layout and map export; and
- Microsoft Excel for tabular summaries and comparison charts.

---

## 5. Coordinate Reference Systems and Spatial Resolution

The original spatial datasets were handled in:

- **EPSG:4326 — WGS 84** for geographic coordinates.

For area calculations, the flood raster and district layers were reprojected to:

- **EPSG:32645 — WGS 84 / UTM Zone 45N**.

The final analysis raster had a spatial resolution of:

- **30 m × 30 m**

Therefore, each raster pixel represented:

**900 m² = 0.0009 km²**

Nearest-neighbour resampling was used during raster reprojection to preserve the binary flood-class values.

---

## 6. Methodology

### 6.1 Extraction of Khulna Division Districts

The Bangladesh district boundary layer was filtered using the division attribute to identify districts belonging to Khulna Division. The selected districts were exported as a separate vector dataset.

The selection criterion used in QGIS was:

```text
"ADM1_EN" = 'Khulna'
```

This produced the 10 districts forming Khulna Division.

### 6.2 Creation of the Khulna Division Boundary

The selected district polygons were dissolved without using a dissolve field, creating a single division-level boundary. This dissolved boundary was used as the spatial mask for flood-raster clipping.

### 6.3 Flood Raster Clipping

The 2024 binary flood raster was clipped using the dissolved Khulna Division boundary with the QGIS **Clip Raster by Mask Layer** tool. This restricted the analysis to the study area.

### 6.4 Raster Reprojection

The clipped raster was reprojected from EPSG:4326 to EPSG:32645 using:

- **Resampling:** Nearest Neighbour
- **Output resolution:** 30 m

The resulting raster contained two values:

- `0` = non-flood/background
- `1` = flood

### 6.5 Total Flooded Area Calculation

The raster unique-values report identified:

- Flood pixels (`Value = 1`): **142,024**
- Pixel area: **900 m²**

The total flood-affected area was calculated using:

```text
Flooded Area (km²) = Flood Pixel Count × 0.0009
```

Thus:

```text
142,024 × 0.0009 = 127.8216 km²
```

The mapped total flooded area was therefore approximately:

**127.82 km²**

### 6.6 District Area Calculation

The district layer was reprojected to EPSG:32645. District area was calculated in QGIS using:

```text
$area / 1000000
```

This converted the polygon area from square metres to square kilometres.

### 6.7 District-wise Flood Statistics

Zonal Statistics was applied using:

- **Zone layer:** Khulna districts
- **Raster:** 2024 binary flood raster
- **Statistic:** Sum

Because flooded cells had a value of `1` and non-flood cells had a value of `0`, the raster sum within each district represented the number of flood pixels.

District-level flooded area was calculated as:

```text
Flooded Area (km²) = flood_sum × 0.0009
```

District-level flood percentage was calculated as:

```text
Flooded Area (%) = (Flooded Area / District Area) × 100
```

---

## 7. Results

### 7.1 Overall Flood Extent

The analysis identified approximately **127.82 km²** of flood-affected area across Khulna Division in 2024.

The total mapped divisional area was approximately **20,749.63 km²**, giving an overall flooded proportion of approximately:

**0.62%**

### Flood Extent Map

![Flood Extent Map](02_Final_Maps/Map_02_Flood_Extent_2024.png)

---

## 8. District-wise Flood Inundation

The district-level analysis revealed strong spatial variability in both absolute flooded area and proportional inundation.

| District | Total Area (km²) | Flooded Area (km²) | Flooded Area (%) |
|---|---:|---:|---:|
| Bagerhat | 3646.18 | 22.50 | 0.617 |
| Chuadanga | 1165.10 | 0.40 | 0.034 |
| Jessore | 2584.93 | 15.58 | 0.603 |
| Jhenaidah | 1956.11 | 0.58 | 0.030 |
| Khulna | 3625.14 | 36.73 | 1.013 |
| Kushtia | 1614.73 | 1.59 | 0.098 |
| Magura | 1048.76 | 1.18 | 0.113 |
| Meherpur | 722.53 | 0.05 | 0.007 |
| Narail | 995.74 | 11.29 | 1.134 |
| Satkhira | 3390.40 | 37.92 | 1.119 |
| **Total / Overall** | **20,749.63** | **127.82** | **0.62** |

### 8.1 Absolute Flooded Area

Satkhira recorded the largest flooded area, with approximately **37.92 km²** classified as flooded. Khulna followed closely with approximately **36.73 km²**, while Bagerhat and Jessore recorded approximately **22.50 km²** and **15.58 km²**, respectively.

At the lower end of the distribution, Meherpur showed the smallest absolute flooded area (**0.05 km²**), followed by Chuadanga (**0.40 km²**) and Jhenaidah (**0.58 km²**).

### District-wise Flooded Area Map

![District-wise Flooded Area](02_Final_Maps/Map_03_District_Flooded_Area_2024.png)

### District-wise Flooded Area Chart

![District-wise Flooded Area Chart](04_Charts/Chart_01_District_Flooded_Area_2024.png)

### 8.2 Flooded Percentage

The proportional inundation pattern differed slightly from the ranking based on absolute flooded area.

Narail had the highest flooded percentage at **1.134%**, followed by Satkhira at **1.119%** and Khulna at **1.013%**.

Bagerhat and Jessore showed intermediate levels of proportional inundation at **0.617%** and **0.603%**, respectively.

The lowest flooded proportions occurred in Meherpur (**0.007%**), Jhenaidah (**0.030%**), and Chuadanga (**0.034%**).

### District-wise Flood Percentage Map

![District-wise Flood Percentage](02_Final_Maps/Map_04_District_Flood_Percentage_2024.png)

### District-wise Flood Percentage Chart

![District-wise Flood Percentage Chart](04_Charts/Chart_02_District_Flood_Percentage_2024.png)

---

## 9. Discussion

The results show that flood exposure was not uniformly distributed across Khulna Division. The southern and south-central districts generally contained larger mapped flood extents than several inland northern districts. Satkhira and Khulna together accounted for a large share of the total mapped flooded area, while Narail showed the highest proportional inundation despite having a smaller absolute flooded area than Satkhira and Khulna.

This difference illustrates why both **absolute flooded area** and **flooded percentage** should be reported. Absolute area indicates the total spatial extent of inundation, while flooded percentage normalizes the result by district size and therefore provides a different perspective on relative exposure.

For example, Satkhira had the largest absolute flooded area, but Narail had the largest inundated proportion. This suggests that district ranking can change depending on whether the analysis focuses on total flooded land or the fraction of each administrative unit affected.

The maps also indicate a concentration of mapped flood pixels in the southern part of the division. However, this project does not independently attribute those spatial patterns to specific hydrological, tidal, rainfall, drainage, or land-use processes. Such causal interpretation would require additional hydrological, meteorological, topographic, and field-based information.

---

## 10. Quality Control and Internal Consistency

The division-wide raster calculation produced:

- **142,024 flood pixels**
- **127.8216 km²** flooded area

The sum of district-level zonal statistics produced approximately:

- **127.8189 km²**

The difference was approximately:

**0.0027 km²**, equivalent to only **3 raster pixels**.

This very small discrepancy is consistent with raster-polygon boundary handling during zonal statistics and does not materially affect the district-level results.

The summed district area was also effectively consistent with the dissolved division-area calculation, with only negligible rounding differences.

---

## 11. Limitations

This project should be interpreted with the following limitations:

1. The analysis is based on a binary flood-extent raster; classification accuracy depends on the quality of the underlying flood-detection process.
2. The 30 m analysis resolution limits representation of very small inundated features.
3. District-level statistics depend on raster-polygon alignment at administrative boundaries.
4. The analysis quantifies spatial inundation but does not estimate flood depth, duration, velocity, damage, population exposure, or economic loss.
5. No independent field validation dataset was incorporated into this repository.
6. Hydrological causes of the mapped inundation were not modelled in this workflow.
7. Large raw Sentinel-1 and intermediate raster datasets are not included in the GitHub repository because of file-size and repository-management considerations.

---

## 12. Reproducibility

The repository contains the final GIS project, processed vector datasets, maps, charts, and final district statistics used in the analysis.

### Repository Structure

```text
Sentinel1-Flood-Mapping-Khulna-2024/
│
├── README.md
│
├── 01_QGIS_Project/
│   └── Khulna_Flood_Mapping_2024.qgz
│
├── 02_Final_Maps/
│   ├── Map_01_Study_Area_Khulna.png
│   ├── Map_02_Flood_Extent_2024.png
│   ├── Map_03_District_Flooded_Area_2024.png
│   └── Map_04_District_Flood_Percentage_2024.png
│
├── 03_Final_Results/
│   ├── Khulna_District_Flood_Statistics_2024.csv
│   └── Khulna_District_Flood_Statistics_2024.xlsx
│
├── 04_Charts/
│   ├── Chart_01_District_Flooded_Area_2024.png
│   └── Chart_02_District_Flood_Percentage_2024.png
│
├── 05_Processed_Data/
│   ├── Khulna_District_Flood_Stats.gpkg
│   ├── Khulna_Districts_UTM45N.gpkg
│   └── Khulna_Division_Boundary_UTM45N.gpkg
│
└── 06_Documentation/
    └── workflow.png
```

---

## 13. Main Outputs

The project generated the following outputs:

- study-area map of Khulna Division;
- Sentinel-1-derived flood-extent map for 2024;
- district-wise flooded-area map;
- district-wise flooded-percentage map;
- district flooded-area comparison chart;
- district flood-percentage comparison chart;
- district-level CSV results;
- formatted Excel results workbook;
- processed GeoPackage layers; and
- a reproducible QGIS project.

---

## 14. Conclusion

This study demonstrates a practical GIS-based workflow for converting Sentinel-1-derived flood information into district-level inundation statistics for Khulna Division, Bangladesh. Approximately **127.82 km²** of the division was mapped as flooded in 2024, representing around **0.62%** of the total mapped area.

The analysis showed important spatial differences among districts. Satkhira had the largest absolute flooded area (**37.92 km²**), whereas Narail had the highest proportional inundation (**1.134%**). Khulna also experienced substantial mapped flooding in both absolute and proportional terms.

The workflow highlights the value of integrating SAR-derived flood extent with administrative boundaries and GIS-based zonal statistics. The resulting maps and quantitative outputs provide a reproducible basis for district-level flood comparison and can be extended in future work using rainfall, elevation, population, land use, flood depth, or damage data.

---

## 15. Future Work

Future extensions of this project may include:

- multi-date Sentinel-1 flood comparison;
- flood-frequency mapping;
- integration with DEM and elevation-derived variables;
- rainfall and river-gauge data;
- population and settlement exposure;
- cropland and land-use impact assessment;
- road and infrastructure exposure;
- flood-depth estimation;
- temporal flood-duration analysis; and
- validation using independent reference or field data.

---

## Author

**Sujoy Biswas**  
Civil Engineering  
Water Resources | GIS | Remote Sensing  

GitHub: [sujoybiswas115](https://github.com/sujoybiswas115)


