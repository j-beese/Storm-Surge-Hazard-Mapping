# Storm-Surge-Hazard-Mapping

A compact geospatial analysis project modelling storm‑surge hazard zones for Hamburg using QGIS and GDAL. The workflow integrates raster classification, hydrological connectivity analysis, dike‑protection filtering, and cartographic generalization to produce four storm‑surge hazard categories based on the official severity guidelines of the City of Hamburg.



The repository includes:



* a reproducible pre-processing workflow
* elevation‑based inundation modelling
* hydrological connectivity derived from public‑domain hydrography
* dike‑protection integration using official flood‑defence data
* dissolved hazard layers for four severity classes
* five final coastal hazard maps suitable for risk assessment, communication, and visualization



All published layers are derived from openly licensed geodata (DL‑DE Zero and DL‑DE BY 2.0) and represent the final, cleaned, validated inundation zones for Hamburg.



# Repository Contents

Repository Contents

* data/ — published GeoPackages (hazard layers, study area, flood defence, connectivity)
* maps/ — final cartographic outputs, available as PNG and PDF file formats
* docs/ — methodology, data sources, attribution, preprocessing notes
* metadata/ — hazard category definitions and map attribution metadata



# Tools used

* QGIS — preprocessing, vector editing, cartography
* GDAL — raster operations, polygonization, dissolving

Data Licensing



# Data Licensing

DL‑DE Zero (public domain) — DGM, hydrography, administrative boundaries

DL‑DE BY 2.0 — dike information (attribution required)

Derived layers are redistributed under the same terms.

