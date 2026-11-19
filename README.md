# Multi-Source Land Use and Land Cover (LULC) Classification Using Google Earth Engine

## Overview

This project develops a multi-source Land Use and Land Cover (LULC) classification for 2025 using Google Earth Engine (GEE) and the Random Forest machine learning algorithm.

The workflow integrates Sentinel-2 optical imagery, Sentinel-1 radar data, SRTM elevation, and ESA WorldCover reference labels to produce a nine-class LULC map at a 10-metre processing scale.

The main objective is to combine different remote sensing datasets and spectral indices to improve land-cover differentiation and generate GIS-ready spatial outputs.

## Study Area
- Study area: Defined using a custom Google Earth Engine boundary asset.
- Mapping period: January–December 2025.
- Mapping scale: 10 metres.

## Datasets Used

| Dataset | Application |
|---|---|
| Sentinel-2 SR Harmonized | Optical satellite imagery |
| Sentinel-1 GRD | VV and VH radar backscatter |
| SRTM DEM | Elevation and slope |
| ESA WorldCover v200 | Reference training labels |

## Methodology

The classification workflow includes:

1. Study area extraction and satellite data filtering.
2. Sentinel-2 cloud masking and median compositing.
3. Spectral index calculation (NDVI, NDWI, MNDWI, NDBI and BSI).
4. Sentinel-1 radar data integration (VV and VH).
5. Terrain variable extraction (elevation and slope).
6. Training sample generation using ESA WorldCover reference classes.
7. Random Forest classification using 300 decision trees.
8. Training and testing sample separation (70:30).
9. Reference agreement assessment using a confusion matrix, Kappa, producer's and consumer's accuracy.
10. Raster-to-polygon conversion and area calculation.

## LULC Classification Scheme

The final classification contains nine land-cover classes:

| Class ID | Land Cover |
|---|---|
| 1 | River / Water |
| 2 | Barren Land |
| 3 | Agriculture |
| 4 | Built-up |
| 5 | Forest |
| 6 | Grassland |
| 7 | Shrubland |
| 8 | Snow / Ice |
| 9 | Wetland |

## Final Outputs

The workflow generates three main GIS products:

- **LULC Raster:** Nine-class GeoTIFF.
- **LULC Polygons:** Polygon Shapefile containing Class_ID, Class_Name and Area_SqKm attributes.
- **Area Statistics:** CSV table showing the area of each land-cover class in square kilometres.

## Tools and Technologies
- Google Earth Engine (GEE)
- JavaScript
- Random Forest Machine Learning
- Sentinel-1 and Sentinel-2
- SRTM DEM
- ESA WorldCover
- GIS and Remote Sensing

## Reproducibility

The complete JavaScript workflow is provided in this repository. Users can run the script in the Google Earth Engine Code Editor after updating the study area asset to their own boundary.

**Validation Note:** ESA WorldCover v200 provides reference labels for training and testing. The reported assessment therefore measures agreement with WorldCover-derived labels, not independent field-based classification accuracy. The resulting 2025 map should be interpreted with this limitation in mind.

## Keywords

LULC Classification, Random Forest, Google Earth Engine, Sentinel-1, Sentinel-2, Multi-Source Remote Sensing, GIS, Land Cover Mapping, Machine Learning.
