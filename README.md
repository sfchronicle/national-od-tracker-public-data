# San Francisco Chronicle / HNP National Overdose Tracker

View the tracker [here](https://www.sfchronicle.com/projects/us-drug-overdose-deaths/).

This repository contains versions of the files that power the overdose tracker.

The data for these files are from the U.S. [Centers for Disease Control and Prevention's National Vital Statistics System](https://wonder.cdc.gov/mcd.html), which researchers recommend as the most reliable source of fatal overdose data for a large-scale, national analysis.

The CDC receives death records from local and state medical officials, such as medical examiners and coroners. The policies and resources of death investigation agencies may affect their ability to detect certain drug types or report fatal overdoses in a timely manner.

Because investigations of fatal overdoses are often lengthy, sometimes taking months to conclude, the most recent data from the CDC reflects an undercount. To account for this, we lag the data, only including deaths through the seventh month prior to the most recent month in the CDC’s dataset. For example, if the CDC has data for at least some of July 2023, we’ll only show numbers from December 2022 and before. The Chronicle’s analysis suggests that death numbers mostly stabilize after this seven-month lag.

The overdose death rates in these files are not age-adjusted, meaning they don’t reflect how a location’s share of younger and older residents — who may be more or less likely to die — could affect the rate.

To identify overdose deaths, we filtered fatalities whose underlying cause was identified as drug poisoning, regardless of whether the overdose was accidental. Fatal overdoses were identified, in keeping with the CDC’s guidance, by filtering for drug poisonings whose underlying cause of death was coded as X40-X44, X60-X64, X85 or Y10-Y14.

In general, deaths reported in these files reflect the location where the death occurred. However, the `drug_waves.csv` file instead tracks fatalities by the victim’s place of residence, as this is the only way the CDC presents deaths that occurred before 2018.

Opioid overdose deaths, as defined by the CDC, are those reported as involving opium, heroin, methadone, a synthetic opioid or another opioid. The CDC does not specify the type of synthetic was involved in the fatality, though through 2022, the vast majority were fentanyl-related. Experts on the CDC’s data believe the proponderance of deaths related to synthetic opioids involve fentanyl.

Death rates are calculated with population estimates from the U.S. Census Bureau. Population estimates for Connecticut’s counties are sourced from the 2020 decennial Census, since the bureau no longer tracks demographic data for those counties.

## File-specific Information

### Overdose deaths by month

The `by_month.csv` file features the number of overdose deaths that have occurred for each month and jurisdiction for which we have data. Jurisdictions include the United States overall, the 50 states, Washington, D.C., counties and independent cities. The data starts in January 2018, and provides a crude death rate (per 100,000 residents) for each month/jurisdiction.

Because recent data may be provisional, death counts and rates from some months may change slightly upon the next release.

### Demographics

The `demographics.csv` file tracks crude death rates by race/ethnicity and jurisdiction. Deaths are from the 12-month period leading up to the most recent month for which we have reliable data. Blank values reflect where deaths totaled fewer than 10 for the parameters; the CDC suppresses values under this threshold.

The demographic categories, defined by the Census Bureau, reflect population estimates of those who identify with a single race and are non-Hispanic, and estimates of Hispanic populations of any race.

### Drug waves

The `drug_waves.csv` file shows the number of deaths (and crude death rate) due to the specific drug class for each state and the country. Deaths are from the 12-month period leading up to the most recent month for which we have reliable data. Some data may be missing due to suppression constraints.

Prescription opioid overdose deaths ("Otheropioids") were identified by filtering for multiple-cause-of-death codes of T40.2 for natural and semi-synthetic opioids and T40.3 for methadone. Deaths involving heroin ("Heroin") have a code of T40.1, deaths involving synthetic opioids excluding methadone ("Fentanyl") have a code of T40.4 and deaths involving methamphetamine and other psychostimulants ("Meth") with abuse potential have a code of T43.6. The CDC estimates that about one-fifth of overdose deaths do not have information on the specific drugs used.

### Yearly data

`The yearly_data.csv` file contains the data presented in the searchable table on the overdose tracker. The data is from the 12-month period leading up to the most recent month for which we have reliable data, and the 12-month period from four years prior to that timeframe. 

The file contains the following columns:
- jurisdiction: The name of a county or independent city (or the overall United States) whose data is being presented in the rest of the row
- state: The name of the state to which the jurisdiction belongs
- deaths_past_year: The number of deaths that have occurred in the jurisdiction over the past year
- crude_rate_past_year: The jurisdiction's crude fatal overdose rate from the past year
- crude_rate_four_years_ago: The jurisdiction's crude fatal overdose rate from the 12-month period four years ago
- synthetics_pct_past_year: The share of overdose deaths from the past year that involved synethetic opioids (which are primarily composed of fentanyl)
- synthetics_pct_four_years_ago: The share of overdose deaths from the 12-month period four years ago that involved synthetic opioids
- population: The jurisdiction's population, sourced from the most recent midyear data from the Census Bureau
