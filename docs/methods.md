\*\*\* Overview \*\*\*

This project models flood hazard zones for Hamburg based on elevation, hydrological connectivity, and dike protection. The workflow combines raster analysis, vector preprocessing, manual masking, and cartographic production. The hazard layers published in this repository represent the dissolved inundation zones for four storm‑surge hazard categories, defined according to the official severity guidelines of the City of Hamburg

(https://www.hamburg.de/politik-und-verwaltung/behoerden/behoerde-fuer-inneres-und-sport/themen/katastrophenschutz/sturmflut-fragen-und-anworten-94034).



\*\*\* Study Area \*\*\*

The study area was derived from publicly available administrative boundary data provided by the Freie und Hansestadt Hamburg under the Datenlizenz Deutschland – Zero – Version 2.0 (DL‑DE Zero).

Source: https://metaver.de/trefferanzeige?cmd=doShowDocument\&docuuid=F35EAC11-C236-429F-B1BF-751C0C18E8B7

The boundary was clipped and refined to define the modelling domain. A derived study\_area\_mask was used internally to restrict inundation modelling to this domain. The mask is not published. The final study\_area.gpkg is included in the public dataset.



\*\*\* Elevation Data \*\*\*

Digital elevation data was sourced from the Digitales Geländemodell Hamburg (DGM) provided by the Landesbetrieb Geoinformation und Vermessung Hamburg. The dataset is licensed under Datenlizenz Deutschland – Zero – Version 2.0 (DL‑DE Zero), placing it in the public domain.

Source:

https://metaver.de/trefferanzeige?cmd=doShowDocument\&docuuid=72C3C8A3-6F6B-48A1-A5C2-2191D4D13196

Raster values were classified into four hazard categories representing increasing water levels. Intermediate rasters and thresholding layers are internal and not included in the repository.



\*\*\* Landmask \*\*\*

A landmask was generated to remove water bodies from the inundation polygons. This mask was derived from the public‑domain hydrography dataset provided by GeoBasis‑DE / BKG under the Datenlizenz Deutschland – Zero – Version 2.0 (DL‑DE Zero).

Source:

https://metaver.de/trefferanzeige?cmd=doShowDocument\&docuuid=72C3C8A3-6F6B-48A1-A5C2-2191D4D13196

The landmask is an internal preprocessing artifact and is not included in the public dataset.



\*\*\* Hydrological Connectivity \*\*\*

Hydrological connectivity was established using the same public‑domain hydrography dataset (DL‑DE Zero). A polyline network was derived from the waterway geometry to identify channels hydrologically connected to the Elbe. This ensured that inundation polygons represent realistic flood propagation paths rather than isolated depressions.

The resulting elbe\_connectivity layer is included in the public dataset.



\*\*\* Flood Protection \*\*\*

Areas protected by dikes and other flood defences were manually masked using the official Deichinformationen Hamburg dataset. A dike\_protection\_mask was created to exclude protected areas from inundation modelling. This mask is internal and not published.



\*\*\* Vectorization and Cleaning \*\*\*

Raster inundation classes were converted to polygons. Fragmented polygons were cleaned, clipped to the study area, and filtered using connectivity and dike protection masks.



// Dissolving

Each hazard category was dissolved into a single MultiPolygon to:



reduce file size

simplify geometry

improve readability

match final cartographic output

The dissolved layers are the ones published in data/.



\*\*\* Final Layers \*\*\*

The final published layers include:



hazard\_combined.gpkg

flood\_defence.gpkg

study\_area.gpkg

elbe\_connectivity.gpkg



All layers were compacted and validated before publication.



\*\*\* limitations \*\*\*



Hydrological Modelling Limitations



QGIS does not provide a physical hydrodynamic or hydrological modelling framework. The workflow used in this project does not simulate water flow, velocity, discharge, or storm‑surge dynamics. Instead, inundation extents are derived from static elevation thresholds combined with hydrological connectivity filtering. As a result, the hazard zones represent potential inundation areas under specified water levels, not a full hydrodynamic simulation.



Connectivity Simplification

Hydrological connectivity is approximated using geometric connectivity, not hydraulic connectivity or flow routing.



Static Water Levels

The hazard categories are based on fixed water‑level thresholds and do not account for temporal dynamics, surge duration, wave action, or compound flooding.

