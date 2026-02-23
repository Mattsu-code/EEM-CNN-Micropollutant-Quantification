# EEM-CNN-Micropollutant-Quantification

This repository contains the data-processing and CNN modeling pipeline for the study:

*Expert-Free Deep Learning of Fluorescence Spectra for Direct Quantification of Organic Micropollutants in Complex Waters*

## License

The code in this repository is licensed under the MIT License. This license applies to the source code only. Raw EEM datasets are not included and remain subject to the terms of the original data provider.

## Data Availability

Raw EEM spectra were obtained from:

Paradina-Fernández, L.; Wünsch, U.; Bro, R.; Murphy, K. Direct Measurement of Organic Micropollutants in Water and Wastewater Using Fluorescence Spectroscopy. ACS ES&T Water 2023, 3(12), 3905–3915. DOI: 10.1021/acsestwater.3c00323

Data repository: DTU Data (DOI: 10.11583/DTU.24440110)

To comply with data use terms, raw spectral files are not distributed in this repository. Users must download the original dataset directly from the DTU Data repository and accept its terms of use.


## Dataset Preparation

The original dataset contains replicate measurements. To ensure sample independence and avoid artificial inflation of model performance, the final modeling dataset comprises:

- 39 natural water samples (metadata in `Natural_water/metadata_natural_water.csv`)
- 67 wastewater samples (metadata in `Wastewater/metadata_wastewater.csv`)
- Total N = 106 samples spanning spiked concentrations from 0 to 50 μg L⁻¹ for ciprofloxacin (CIP), naproxen (NAP), and zolpidem (ZOL)

**Construction of Concentration Labels:**
The provided metadata files list the **spiked concentrations**. For wastewater samples, the modeling targets (ground truth) correspond to the **total concentrations**, calculated by adding the intrinsic background concentration to the spiked value. Background levels were sourced from *Paradina-Fernández et al.* (including data digitized from figures). Specifically:
- Background concentrations below 0.4 μg L⁻¹ were considered negligible (treated as 0 μg L⁻¹).
- For literature-reported concentration ranges, the **midpoint of the range** was used.
- Natural water samples were treated as having zero background for the target micropollutants.

The final dataset spans total concentrations from 0 to 50 μg L⁻¹ for ciprofloxacin (CIP), naproxen (NAP), and zolpidem (ZOL).

**Data Cleaning & Preprocessing:**
- Sample `eff_cip4` (CIP = 37.5 μg L⁻¹) was excluded from modeling due to anomalous prediction behavior.
- For samples `inf_zol1`–`inf_zol6`, the emission range ends at 451.6 nm (vs. 610.4 nm for other samples) but fully covers the ZOL fluorescence signal. The missing high-wavelength region was filled using the unspiked influent sample `inf_cip16` to maintain consistent input tensor dimensions.


## Reproduction Instructions

1. Download the raw dataset from DTU Data (DOI: 10.11583/DTU.24440110)
2. Place the downloaded Natural_water/ and Wastewater/ directories in the root of this repository
3. Install dependencies
4. Open and execute EEM_OMPs_DL.ipynb in Jupyter Lab


## Results Visualization
Model performance was assessed using repeated 5-fold cross-validation (5 repeats, 25 folds total), with folds constructed to ensure balanced representation of both water matrix types (natural water and municipal wastewater) in each training–test split—an approach implemented via stratification on a binary domain label.



<img width="2638" height="910" alt="image" src="https://github.com/user-attachments/assets/c20d81f2-25bc-42b3-8f89-8c38c755a645" />



This visualization enables clear assessment of model performance across different sample types and water matrices, with R² values reported for each compound (CIP, NAP, ZOL) in the plot titles. 
Natural water samples are shown as circles (○), municipal wastewater as squares (□); solid symbols denote samples with one target OMP, open symbols denote samples with 2–3 target OMPs, and crosses (×) denote samples without target OMPs (light blue: NW, light orange: WW). The dashed black line indicates ideal 1:1 agreement; gray dash-dotted lines represent ±20% relative deviation from the true value. The light gray shaded region highlights the ±10% relative error envelope.




## Citation

If this code is used in your research, please cite: *Expert-Free Deep Learning of Fluorescence Spectra for Direct Quantification of Organic Micropollutants in Complex Waters*

And the original dataset:

Paradina-Fernández, L.; Wünsch, U.; Bro, R.; Murphy, K. Direct Measurement of Organic Micropollutants in Water and Wastewater Using Fluorescence Spectroscopy. ACS ES&T Water 2023, 3(12), 3905–3915.
