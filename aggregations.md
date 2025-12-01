# Download data

## Files

We provide two different aggregations:

1. **County-total aggregation**: This represents the total amount of spending for assistance to households in a county (or county-equivalent), without regard to the date of payment (but excluding any payments known to be made after March 31, 2023). There is one observation per county.

2. **County-month aggregation**: This represents the total monthly spending for assistance to households in a county (or county-equivalent) for each month from January 2021 through March 2023. Thus, there are multiple observations per county.  

Two quantities are calculated for each observation: 

1. The sum of the dollar amount paid for assistance, and
2. The number of unique addresses assisted.

Both these quantities are aggregated without regard to assistance type or payee type (e.g., landlord, tenant). Small values (fewer than 11 unique addresses per observation and the corresponding dollar amount for that observation) are suppressed.

The data between the two aggregations are not directly comparable, for the following reasons:

1. Some grantees submitted data with missing or poor-quality payment dates; these grantees' payments could not be included in the county-month aggregation but could be included in the county-total aggregation. Therefore, some counties appear in the county-total aggregation but not in the county-month aggregation.
2. Additionally, the ERA2 data source used for some grantees differs between aggregations, again due to data quality variations for the payment date field.
3. Small counts suppressed at the county-month level are aggregated into the total value at the county-total level.

## Data dictionary 

The columns for the aggregated files are described below.

- `county_geoid_coalesced`: The Census GEOID (i.e., FIPS code) for the geographic county or county-equivalent. Note: the county geographies are vintage 2020; in Connecticut, these refer to the pre-2022 county-equivalents.
- `month_of_payment`: *For county + month aggregation only*. The calendar month of the payment, as recorded by grantees. Format is YYYY-MM-DD (DD being `01` in all cases).
- `sum_assistance_amount`: The sum of non-negative payments in the cell, for any type of assistance to households. Values are nominal US dollars. Suppressed with value `-99999` if value of `unique_assisted_addresses` was less than 11.
- `unique_assisted_addresses`: The count of unique addresses (taking into account unit numbers) assisted in the cell. Suppressed with value `-99999` if value was less than 11.

## User notes and data limitations

The PHPDF data were compiled by Treasury from hundreds of independent submissions made by ERA grantees to Treasury. In total, 400 state and local ERA1 grantees and 373 state and local ERA2 grantees accepted allocations for ERA. Compliance with Treasury's [reporting requirements](https://home.treasury.gov/policy-issues/coronavirus/assistance-for-state-local-and-tribal-governments/emergency-rental-assistance-program/reporting) was not universal at the time of the data collection; some grantees had not reported any data, while others had submitted data nonconformant with Treasury's published data standards. Therefore, users should be aware that this dataset does not represent complete coverage of ERA spending across the nation.

We highlight the following data limitations:

- **Many grantees who participated in ERA are not represented in the data** due to data missingness or quality issues. The county-month dataset reflects reports from 196 grantees (48% of grantees). The county-total dataset reflects reports from 205 grantees (51% of grantees). The drop-off is due to data non-submission (15% of grantees), poor-quality data (6% for county-month, 3% for county-total), spending amounts inconsistent with allocation amounts (10%), and geographic overlap with grantees that did not pass the preceding thresholds (20%).
- **Missing grantees may affect entire geographies** even if other grantees serving that geography have good data quality; for example, if a state grantee is missing, every county in that state will be missing. The county-month dataset includes 2,308 county-equivalents (73% of county-equivalents, 63% of U.S. renter population), while the county-total dataset includes 2,364 county-equivalents (75% of county-equivalents, 65% of U.S. renter population). But please note that small-population counties may have all cells suppressed due to a low count of unique addresses in that county.
- **Not every payment made by a grantee may have been reported by the grantee**. Particularly for ERA2, grantees were required to submit cumulative data up to the reporting period, but not all may have done so. We threshold the data to drop grantees unlikely to be reporting full data, but this may not have screened out every such grantee.
- **Grantees may have reported addresses for the payee** (landlord or utility), even though they were required to report addresses for the assisted property. We excluded payments made outside of the geographic jurisdiction of the grantee, since these payments by definition do not record the address of the assisted household, but this may not have filtered out all misreported addresses.
- **Up to 20% of a grantee's records may be dropped** due to data quality issues (for example, missing payment amounts), while still passing our data quality thresholds. Users should consult the data coverage tables included [here](data_coverage_descriptives.qmd#grantees-included-with-less-than-90-variable-quality) for a list of these grantees.
- **The months in the county-month aggregation refer to dates of payment, not dates of assistance**. Payments could address both arrears and forward rent, so payment months should not be conflated with months over which households were assisted.
- **Grantees differed in how they structured their payments**. Some may have made a separate payment for each month of assistance, while others may have made one payment for the entire duration of assistance. Therefore, an address which received 3 months of forward rent could show up across 3 months if the grantee made 3 separate payments, or across one month if the grantee made one payment for all three months.
- **Counties containing a large share of missing-address records may have an inflated count of unique assisted addresses**. This was because records which could be located to a county but did not include address information were treated as unique for the purpose of counting unique addresses. Users should consult the data coverage tables included [here](data_coverage_descriptives.qmd#counties-with-high-share-of-missing-addresses) for a list of these counties.
- **Jurisdictions outside of the 50 states and Washington, D.C., are not included** due to geocoding difficulties for addresses in U.S. territories.
- **Payments made by Tribal grantees are not included**, because they did not submit PHPDF data.
- **Dollar amounts reported are nominal values** and are not adjusted for inflation.

For more information on which grantees and records are included in the aggregation, please refer to the data coverage descriptives provided [here](data_coverage_descriptives.qmd).

## Download

The aggregated data files may be found as CSV's at this project's public Github repository, [here](https://github.com/housinginitiative/era-county-level-dataset-public/tree/main/data/aggregated_data).

Potential users of these data are highly encouraged to review the list of limitations above and to inspect the [data coverage descriptives](data_coverage_descriptives.qmd) in light of their particular needs.
