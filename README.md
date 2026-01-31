 Monthly Baseflow Index (BFI) — 9 Methods (No Drainage Area Required)

This repository computes **monthly Baseflow Index (BFI)** for multiple gauging stations using **nine** widely used baseflow-separation methods implemented in the `baseflow` Python package.

It is designed for **daily streamflow time series in “wide CSV” format** (one `time` column + one column per station), and produces:

- **Monthly BFI time series** for each station and method  
- A **combined long-format** monthly BFI table for multi-station analysis  
- **Comparison plots** (methods vs time; and mean seasonal cycle)

---

## Why 9 methods?

Some baseflow separation methods (HYSEP family: fixed/sliding/local minima) require **drainage area** to define the separation window length. If you do **not** have drainage area consistently for all stations, this repo uses the **9 methods that do not require drainage area**:

**Methods included (9):**
- `UKIH`
- `LH` (Lyne–Hollick filter)
- `Chapman`
- `CM`
- `Boughton`
- `Furey`
- `Eckhardt`
- `EWMA`
- `Willems`

---

## Monthly BFI definition

For each station and method, daily baseflow \(Q_b(t)\) is estimated first. 
Key implementation details:
- Daily negative/invalid discharge values are treated as missing.
- Monthly BFI is computed only if a month has at least `min_days_per_month` valid daily observations (default: **15 days**).
- Monthly BFI is clipped to \([0, 1]\) after aggregation for stability.

---


