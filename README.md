# EEM-CNN-Micropollutant-Quantification
This repository contains the complete data-processing and modeling pipeline used in our study *"Expert-Free Deep Learning of Fluorescence Spectra for Direct Quantification of Organic Micropollutants in Complex Waters"*. 
Data processing and CNN modeling pipeline for quantifying organic micropollutants from EEM fluorescence spectra (based on Paradina-Fernández et al. 2023 dataset). Raw data must be obtained from DTU Data (DOI: 10.11583/DTU.24440110).

> ⚠️ **License Scope Notice**  
> This repository is licensed under the [MIT License](LICENSE) **for code only**.  
> Raw EEM datasets are **NOT included** and remain governed by the [DTU Data Terms of Use](https://doi.org/10.11583/DTU.24440110).
---

## 🔒 Data Availability
Raw EEM spectra were obtained from:
> Paradina-Fernández et al. (2023), *ACS ES&T Water* 3(12):3905–3915  
> Data Repository: [DTU Data (DOI: 10.11583/DTU.24440110)](https://doi.org/10.11583/DTU.24440110)
> The original dataset contains numerous parallel (replicate) measurements. To ensure sample independence and avoid artificial inflation of model performance, the final dataset includes 39 natural water (Table S1) and 67 wastewater samples (Table S2) (total N = 106), spanning spiked concentrations from 0 to 50 μg L-1 for each analyte. 


**To reproduce results**:  
1. Download raw data directly from DTU Data (accept their terms)  
2. Place `Natural_water/` and `Wastewater/` folders in this repository root  
3. Run `EEM_OMPs_DL.ipynb` in Jupyter Lab

<img width="2117" height="735" alt="image" src="https://github.com/user-attachments/assets/a586a153-4644-4581-b870-fdd64925127a" />
