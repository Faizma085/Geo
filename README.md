# Monthly Baseflow Index (BFI) — Six-Method Ensemble

This repository computes **monthly Baseflow Index (BFI)** from daily streamflow using six hydrograph-separation methods:

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
python bfi.py "Sample.csv" --output-dir results
```

With drainage-area metadata:

```bash
python bfi.py "Sample.csv" --area-csv station_area.csv --output-dir results
```

## Outputs

```text
six_method_BFI_summary.csv
six_method_monthly_ensemble.csv
```

## Requirements

```bash
pip install numpy pandas
```
