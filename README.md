# Fenton Birthweight Percentiles (SAS Macro)

Compute sex- and gestational-age–specific **Z-scores and SGA/AGA/LGA designation** using the LMS method and Fenton preterm references.

---

## Overview
This repo contains a SAS macro to calculate birthweight Z-scores and SGA/AGA/LGA (small for gestational age, average for gestational age, large for gestational age) designation for preterm infants.

Excel and web-based versions of the calculator are available at www.ucalgary.ca/fenton.

This calculator is intended for assessing size at birth only and should not be used for postnatal growth assessment. Infants are often categorized as being small, appropriate and large for gestational age based on their weight percentiles, which can be incorrect for the individual. Infants can be small due to slow intrauterine growth and/or smaller genetic size and higher weights due to maternal health conditions and/or larger genetic size. Always interpret results within the clinical context.

Source:
Fenton TR, Kim JH. A systematic review and meta-analysis to revise the Fenton growth chart for preterm infants. BMC Pediatr. 2013;13:59. 
Paper is available free with open access from:
http://www.biomedcentral.com/1471-2431/13/59

---

## Requirements
**Input data (one row/infant):**
 - Gestational age in completed weeks (e.g., 36 weeks + 0 days and 36 weeks + 6 days should both be recorded as 36). The valid date is 22-42 weeks; scores for gestational ages less than 22 weeks or greater than 42 weeks will not be calculated.
 - Sex coded 1 for male, 0 for female
 - Weight in grams. Decimal values are permitted.

---

## Macro Usage
```sas
libname mymacros 'C:\Path\To\Fenton';
options mstored sasmstore=mymacros;

%fenton(dataset, sex, ga, weight);
```

The macro will output a dataset called fenton that contains:

 - All original variables from the input dataset
 - Wt_class: classification based on gestational age and sex
     - 'SGA' - weight < 10th percentile
     - 'AGA' - weight between 10th and 90th percentile
     - 'LGA' - weight > 90th percentile
 - Z_wt: weight-for-gestational-age Z-score calculated using the LMS method
 - pct_wt: weight-for-gestational-age percentile, converted from the Z-score


---

## License and Use

This macro is provided for academic and clinical research purposes only.
No warranty is expressed or implied. Users are responsible for validating the results for their specific application.

This macro incorporates reference standards from:
Fenton TR & Kim JH, BMC Pediatr, 2013, used here under fair use for educational and research purposes.

Do not redistribute in commercial software or alter the embedded reference data.

---

*Last updated: 2025-08-12*
