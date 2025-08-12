# Fenton Birthweight Percentiles (SAS Macro)

Compute sex- and gestational-age–specific **Z-scores and SGA/AGA/LGA designation** using the LMS method and Fenton preterm references.

---

## Overview
This repo contains a SAS macro to calculate birthweight Z-scores and SGA/AGA/LGA (small for gestational age, average for gestational age, large for gestational age) designation for preterm infants.

---

## Method (LMS)
For birthweight \(y\) and reference parameters \((L,M,S)\):
\[
Z =
\begin{cases}
\frac{(y/M)^L - 1}{L\cdot S}, & L \neq 0 \\
\frac{\ln(y/M)}{S}, & L = 0
\end{cases}
\qquad
\text{Percentile} = 100 \times \Phi(Z)
\]
Interpolation (default) linearly blends \(L,M,S\) across fractional weeks.

---

## Requirements
**Input data (one row/infant):**
- `sex` (`1` Male, `0` Female)
- `ga_var` (gestational age reported in full, completed weeks)
- `weight_var` (birth weight reported in grams)

---

## Macro Usage
```sas
libname mymacros 'C:\Path\To\Fenton';
options mstored sasmstore=mymacros;

%fenton(dataset, sex, ga, weight);
```

---

## Citation
- Fenton TR, Kim JH. *BMC Pediatrics.* 2013;13:59. doi:10.1186/1471-2431-13-59  

---

*Last updated: 2025-08-12*
