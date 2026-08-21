# BFI-Six-Method Ensemble

This repository computes **monthly BFI** from daily streamflow using six hydrograph-separation methods:

* Lyne-Hollick
* UKIH
* HYSEP fixed interval
* HYSEP sliding interval
* HYSEP local minimum
* Eckhardt

The input should be a wide CSV containing one `time` column and one column per gauging station.

## Method

Daily baseflow is estimated independently using all six methods. Monthly values are retained only when at least **90% of expected daily observations** are available.

The monthly ensemble baseflow is calculated as the **median of the valid method-specific monthly baseflow estimates**, with at least **4 of 6 methods** required.

## Input example

```text
time,St1,St2,St3
2004-01-01,12.5,8.4,15.1
2004-01-02,11.8,8.1,14.7
```

## Run

```bash
python bfi_6.py "Sample.csv" --output-dir results
```

With drainage-area metadata:

```bash
python bfi_6.py "Sample.csv" --area-csv station_area.csv --output-dir results
```
```

## Requirements

```bash
pip install numpy pandas
```
# Data and Code Availability

This repository contains the basic code associated with the manuscript.

## Data availability

The original datasets used in this study are not redistributed through this GitHub repository because several datasets are large and/or are subject to the distribution conditions of their original providers.

All datasets used in the analysis are publicly available from their original sources. Dataset names, references, access links, and other relevant information are provided in the **Supplementary Information** accompanying the manuscript. These links can be used to download the original data directly from the respective data providers.

Where applicable, users should follow the licence, citation, and terms-of-use requirements specified by each original data provider.

## Reproducibility

The code in this repository documents the main processing and analysis procedures used in the study. Reproduction of the analyses requires downloading the relevant datasets from the sources listed in the Supplementary Information and organizing them according to the input structure expected by the scripts.

## Contact

For questions about data access, file organization, or reproduction of the analyses, please contact the **corresponding author** using the email address provided in the manuscript.


## Citations
Faiz et al. will be available upon acceptance for publication. It is advised to cite the paper if the method or data has been used ...

Please note that requests for assistance do not replace the access conditions established by the original data providers.
