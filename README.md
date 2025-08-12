# Fenton Birthweight Percentiles (SAS Macro)

Compute sex- and gestational-age–specific **Z-scores and SGA/AGA/LGA designation** using the LMS method and Fenton preterm references.

---

## Overview
This repo contains a SAS macro to calculate birthweight Z-scores and SGA/AGA/LGA (small for gestational age, average for gestational age, large for gestational age) designation for preterm infants.

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
