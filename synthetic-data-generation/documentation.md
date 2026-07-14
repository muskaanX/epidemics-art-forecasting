# India ART Synthetic Dataset Documentation

## Overview

Synthetic monthly drug consumption dataset for 7 antiretroviral drugs in India. Coverage: August 2015 to March 2024 (104 months). Generated for research and modeling purposes.

Drugs: ABC+3TC adult, AZT+3TC adult, ATV/r adult, DRV/r adult, ABC+3TC pediatric, AZT+3TC pediatric, LPV/r pediatric.

## Patient Count Methodology

Annual patient counts derived from NACO-published line-wise ART data at 9 anchor points (FY 2015-16 through FY 2023-24). Regimen-wise shares applied to produce drug-level patient counts. Monthly values generated via linear interpolation between annual anchors. Gaussian noise and discrete spikes applied to simulate real-world reporting variability.

Third-line counts estimated via ratio interpolation: third-line/second-line ratio linearly interpolated from 0% (2016-17) to 4.63% (2019-20).

Pediatric second-line counts derived using child share of ART (CLHIV/PLHIV ratio from India HIV Estimates).

## Regimen Shares

Regimen shares are qualitative estimates grounded in NACO treatment guideline transitions.

- NACO 2013 guidelines: AZT+3TC+NVP/EFV was preferred first-line. AZT+3TC first-line share estimated at 0.15 for the 2015-18 period, reflecting legacy cohort plus TDF-contraindicated new patients.
- NACO 2017 guidelines: TDF+3TC+EFV became preferred. AZT+3TC downgraded to alternative (TDF contraindications only). Published TDF contraindication rate in HIV populations is 5-10%. First-line AZT+3TC share estimated at 0.075 for 2019-21, consistent with this range.
- NACO 2021 guidelines: TDF+3TC+DTG (TLD) became preferred. AZT+3TC further marginalised. First-line share estimated at 0.035 for 2022-24.

ATV/r phase-out reflects documented transition from ATV/r to DRV/r in second-line protocols. DRV/r carries 1.0 share of third-line throughout as it is the only third-line PI used in India's public program.

## Dosage Calibration

Patient counts converted to monthly consumption using WHO weight-band dosing guidelines (NBK572728).

Adults:
- ABC+3TC: 30 tablets/month (600/300mg once daily)
- AZT+3TC: 60 tablets/month (300/150mg twice daily)
- ATV/r: 30 tablets/month (ATV 300mg once daily)
- DRV/r: 60 tablets/month (DRV 600mg twice daily, treatment-experienced dosing)

Pediatric doses are weighted averages across WHO weight bands. Weight band ratios for ABC+3TC and AZT+3TC (3-<6kg, 6-<10kg, 10-<14kg, 14-<20kg, 20-<25kg): 0.05, 0.10, 0.25, 0.40, 0.20. Weight band ratios for LPV/r (10-<14kg, 14-<20kg, 20-<25kg): 0.30, 0.50, 0.20. These ratios reflect declining new infection rates in younger/lighter children and higher representation of older children in India's active ART cohort.

- ABC+3TC pediatric: 138 tablets/month (60/30mg, twice daily) before April 2022; 69 tablets/month from April 2022 (120/60mg formulation, WHO prequalified April 2022).
- AZT+3TC pediatric: 138 tablets/month (60/30mg, twice daily).
- LPV/r pediatric: 111 tablets/month (100/25mg, asymmetric dosing for lower weight bands).

Pediatric weight band ratios informed by IeDEA global weight-for-age distributions and India-specific age-at-diagnosis data (median ~10 years, 73% above 5 years).

## Known Limitations

1. Monthly values between annual anchor points are interpolated. No monthly public data is available to validate against.

2. Adult consumption assumed to be in pill count format throughout the series. Evidence suggests a reporting transition from patient count to pill count occurred for some drugs between 2016-2018. This transition is not modelled.

3. A sharp decline in CLHIV estimates between 2016-17 and 2017-18 (133,000 to 61,000) reflects a Spectrum model revision, not a real demographic change. This creates an artifact in pediatric drug consumption around that period.

4. Pediatric weight band distributions use global IeDEA data. India-specific distributions are not publicly available.

5. AZT+3TC adult consumption may be over-estimated due to uncertainty in the size of the residual first-line cohort post-2017 TDF transition. Publicly available data does not allow this to be resolved precisely.

## Sources

WHO dosing tables (antiretroviral drugs for children): https://www.ncbi.nlm.nih.gov/books/NBK572728/

WHO prequalification of ABC/3TC 120/60mg dispersible tablet (Micro Labs Ltd, April 2022): https://extranet.who.int/prequal/news/paediatric-dispersible-abacavirlamivudine-tablet-prequalified

IeDEA weight-for-age distributions in children on ART: https://pmc.ncbi.nlm.nih.gov/articles/PMC7245795/

IeDEA Asia-Pacific ART initiation characteristics (age at initiation, underweight prevalence): https://pmc.ncbi.nlm.nih.gov/articles/PMC10501581/

India pediatric HIV cohort, age at diagnosis: https://pmc.ncbi.nlm.nih.gov/articles/PMC4297378/

IAP 2015 growth charts for Indian children (weight reference): https://pmc.ncbi.nlm.nih.gov/articles/PMC4481652/

NACO National Guidelines for HIV Care and Treatment 2021: https://naco.gov.in/national-guidelines-hiv-care-and-treatment-2021
