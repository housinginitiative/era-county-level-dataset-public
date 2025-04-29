# County Emergency Rental Assistance Spending: An Introduction to the Project

![](images/combined_logo.png)

## Background

The federal Emergency Rental Assistance (ERA) program was administered by the U.S. Department of the Treasury to alleviate the impact of the COVID-19 pandemic on renter households.

A total of $46.55 billion was appropriated for two programs: ERA1 ($25.55 billion authorized in December 2020 as part of the Consolidated Appropriations Act of 2021) and ERA2 ($21 billion included with the American Rescue Plan Act, passed March 2021). The funds were allocated to grantees who administered their own programs, subject to program requirements set by Treasury. Grantees included states, U.S. territories, Washington D.C., and large-population counties and cities. For ERA1, tribes and the Department of Hawaiian Home Lands were also grantees.

Over the course of the two programs, ERA funds could be used to address various housing needs for low-income renters. For the purposes of this project, we focus on assistance paid by grantees to address rent (forward and in arrears), utility costs (forward and in arrears), and 'other housing-related expenses' as defined by Treasury (such as relocation expenses). Assistance could be paid either to tenants, landlords, utility companies, or providers of housing-related expenses. Further details on eligibility requirements and programmatic guidance for ERA can be found on [Treasury's web site](https://home.treasury.gov/policy-issues/coronavirus/assistance-for-state-local-and-Tribal-governments/emergency-rental-assistance-program) for ERA.

This dataset details aggregate ERA spending at the county-month level and the county-total level, based on payment data submitted by ERA grantees to Treasury as part of their periodic reporting responsibilities. We attempted to establish broad coverage across the nation, aiming to share these data publicly with researchers interested in applying ERA payments data to their own research. The ERA program was ongoing and ERA funds had not been fully expended at the time of this project’s implementation. The dataset may be updated once the ERA program is fully closed out and more complete data are available. 

This project was completed by a team comprising of the [Housing Initiative at Penn](https://www.housinginitiative.org/), the [Eviction Lab](https://evictionlab.org/) (Princeton University), and [Urban Displacement Project](https://www.urbandisplacement.org/) (University of California, Berkeley), partially in fulfillment of an award from the U.S. Department of Housing and Urban Development. The project was also supported by grant R01NR020854 (MPI Eisenberg and Pollack). Hepburn's involvement is supported by R01NR020748.

The project team is solely responsible for the analytical decisions made in this project and the accuracy of aggregated files produced by this project. This work does not reflect the views of the U.S. Government or any other funding sources.

### Data Citation

The aggregate data produced by this project may be cited as:

Kim, Chi-Hyun, Grace Hartley, Jacob Haas, Tim Thomas, Rebecca Yae, and Peter Hepburn. County Emergency Rental Assistance Spending. 2025. Accessed via https://housinginitiative.github.io/era-county-level-dataset-public/.

## Data sources

### PHPDFs

The main sources of data for this project were confidential ERA participant household payment data files (PHPDFs), which ERA grantees were required to report to Treasury on a periodic basis.[^1] PHPDFs were required to include payment-by-payment details on how ERA funds were distributed, including: amounts and dates of payments, addresses of the assisted property, type of assistance covered by the payment (e.g., rent arrearage), and type of payee (e.g., landlord). However, while Treasury published uniform data reporting requirements, each grantee had its own mechanisms for data collection and management. Once submitted, these reports were compiled by Treasury into a large file for each reporting period, separately for ERA1 and ERA2. The project team received these data between August 2023 and May 2024, and the datasets available here are based on the payments data as they existed at that point in time.

[^1]: Tribal grantees and the Department of Hawaiian Home Lands were exempt from reporting payment-level data, and their payments are not reflected in this dataset. There were 293 of these grantees, with $843,790,377.72 in total allocations.

For ERA1, Treasury compiled a closeout PHPDF based on the payments reported by grantees for the entirety of the ERA1 period of performance ending on December 29, 2022. This forms the basis of the ERA1 payments data used in this analysis.

ERA2 was still ongoing through 2023, with its period of performance ending on September 30, 2025. Grantees were required to submit data on a quarterly basis, reporting cumulative payments made from the beginning of ERA2 up to the end of the reporting period. We generally use the PHPDF for the 2023 Q4 reporting period, but supplement with data reported in earlier quarters in 2023 for grantees with good data quality in those files but with poor-quality or missing data in the Q4 file.

Whether the ultimate source of the assistance was ERA1 or ERA2 was largely immaterial for tenants and landlords, so our final aggregation does not distinguish between them. However, the two programs had slightly different administrative and reporting requirements, so for the purposes of our data processing pipeline, ERA1 and ERA2 are treated separately until just before the final aggregation.

Addresses in PHPDFs were primarily geocoded by HUD, except for a small percentage of records which failed HUD's geocoding. These records (77 records in ERA1 and 24,394 records in ERA2) were geocoded by the project team using the Census geocoder.

### Other data

We also made use of ancillary files, including:

- A crosswalk of grantees for ERA1 and ERA2 compiled by the National Low Income Housing Coalition
- Treasury's publicly released aggregate summary expenditure files ([ERA1](https://home.treasury.gov/system/files/136/Q1-2021-Q4-2022-ERA-Demographic-Data.xlsx), [ERA2](https://home.treasury.gov/system/files/136/ERA2-Cumulative-Program-Data-Q2-2021-Q3-2024.xlsx))
- Treasury's updated list of allocation amounts (including any reallocations made through June 2024)
- HUD's [ZIP code/county crosswalk](https://www.huduser.gov/portal/datasets/usps_crosswalk.html)
- A county/city population crosswalk generated from the [Geocorr engine](https://mcdc.missouri.edu/applications/geocorr.html)

## Contact

For any questions regarding this project, please contact Chi-Hyun Kim at chkim@design.upenn.edu, or any of the three project organizations ([HIP](mailto:housinginitiative@design.upenn.edu), [Eviction Lab](mailto:info@evictionlab.org), [UDP](mailto:info@urbandisplacement.org)).
  








