# dust_aerosol_analysis_aerose2015
Quantify the relationship between AEROSE dust sources and elemental signatures using back-trajectory analysis, elemental analysis, and Pearson Correlation. 

## Summary of Repository 
This repository provides 2015 AEROSE Campaign data resources and code for the forthcoming publication: *Yeager, D. E. and Morris, V. R. (in press). Distinguishing Saharan Dust Plume Sources in the Tropical Atlantic Using Elemental Indicators. MDPI Atmosphere (2024).*

## Goal of the Study 
This study distinguishes source region elemental signatures of Saharan dust aerosols sampled during the **2015 Aerosols Ocean Sciences Expedition (AEROSE)** in the tropical Atlantic. **Inductively Coupled Plasma Mass Spectrometry (ICP-MS)** analysis differentiated metal isotope concentrations of AEROSE filter samples during dust sampling periods. **Back-trajectory analysis** and NOAA satellite aerosol optical depth retrievals identified source regions of AEROSE dust samples collected in 2015. The relationship between these sources and dust isotopes was quantified using **Pearson Correlation** statistics.

## Datasets
### Available directly in repository provided by the university labs
**Note:** Direct source not publicly available.
- University of Miami
  - Ship navigation data (2015_Alliance_GPS_ShipData.dir)
  - Radiation data (M-AERI Radiances_15.dir)
- University of Maryland County Baltimore
  - Processed isotope data for dust samples (Isotope_Conc_Aerose15_DY-5.xlsx

### Publicly available for direct download 
- Sun-photometer data (AERONET-MAN website)
  - https://aeronet.gsfc.nasa.gov/new_web/cruises_new/Alliance_15.html
- VIIRS satellite data (NASA LDAAS website)
  - https://ladsweb.modaps.eosdis.nasa.gov
- NOAA HYSPLIT: Back-trajectory
  - https://www.ready.noaa.gov/HYSPLIT.php

## Task & Code Reference
### 1. Classify dust events using M-AERI & sun-photometer observations:  
  1.1 **Dust ID.py**: Extract ship locations from M-AERI GPS data. 
  - Inlcudes data preprocessing procedure includes extracting, averaging, and band ratioing the radiance data. 
   
**Input Data:**

- *M-AERI Radiances_15.dir*: M-AERI radiance data
  - Directory Path: /AEROSE Data Archive/2015 AEROSE/MAERI Radiances_15/
- *2015_Alliance_GPS_ShipData.dir*: M-AERI navigation data
  - Directory Path: /AEROSE Data Archive/2015 AEROSE/2015_Alliance_UMiami_data/2015_Alliance_GPS_ShipData/
- *AOD/Alliance_15_all_points.lev20*: AERONET-MAN Sun-photometer
  - Directory Path: /AEROSE Data Archive/2015 AEROSE/Alliance_15-2/AOD/Alliance_15_all_points.lev20

**Output Data:**
- *NavData1 (dataframe)*: A dataframe that includes hourly latitude, longitude of the ship location.
    - Hourly ship location
### 2. Conduct the Dust Filter Elemental Analysis:
  2.1 **Element_w_errorbar.py:** Extract and plot elemental isotope data from inductively coupled plasma mass spectrometer data. 
  2.2 **Element_w_errorbar.py:** Perform Pearson Correlational analysis of source region metrics and elemental data.
  - Create isotope concentration plots 

  **Input Data:** 
- Isotope_Conc_Aerose15_DY-5.xlsx
o	Conduct correlational analysis of isotopes & source region quantifications (“ICP_Conc.py” script)
	Input Data: Isotope_Conc_Aerose15_DY-5.xlsx

### 3. Back-trajectory analysis of dust sources:
  3.1 **Mean_AOT_VIIRS_PSAF.py:** Average VIIRS aerosol optical depth rasters
  
  3.2 **ReferenceVIIRSGrid.py** Retrieve reference grid from raster file
  
  3.3 **BulkTrajHS.py**	Generate a text file for each back-trajectories
  
  3.4 **ReadHYSPLITtxt.py** Read back-trajectories text files
  
  3.5 **IntersectArray.py** Compute back-trajectory intersections
  
  3.6 **Sum_intersections.py** Sum back-trajectory intersections per pixel
  
  3.7 **Mean_AOT_VIIRS_PSAF.py** Compute Potential Source Area Frequency and export as a raster file 




