# Ottowa-Covid-Census-Data

All usable data can be found in `cleaned_data_sets`.

# Description of Data
## Demographic information
**location**: `cleaned_data_sets/census.csv`

demographic information is taken from the [2016 census](https://www12.statcan.gc.ca/census-recensement/2016/dp-pd/prof/details/page.cfm?Lang=E&Geo1=CSD&Code1=3506008&Geo2=PR&Code2=01&SearchText=ottawa&SearchType=Begins&SearchPR=01&B1=All&TABID=1&type=0). Each file in `census_area_code` contains self-described ethnicities of individuals pertaining to the area code. `census.csv` contains all this information aggregated together.

### Extra Notes
This is a total population estimate. The sum of the ethnic groups in this table is greater than the total population estimate because a person may report more than one ethnic origin in the census.
,'Ethnic origin' refers to the ethnic or cultural origins of the person's ancestors. An ancestor is usually more distant than a grandparent. For additional information on the collection and dissemination of ethnic origin data  refer to the [Ethnic Origin Reference Guide  Census of Population  2016](https://www12.statcan.gc.ca/census-recensement/2016/ref/guides/008/98-500-x2016008-eng.cfm).

### Ethnic origins
in this case, ethnic origin was split into primary, secondary, and tertiary. In the original data, each ethnic origin was represented by an individual row, with indents at the beginning of ethnic origin to visually indicate the ethnic origins specificity. For example:

    total ethnic origin in private households
      European origins ...
        British Isles origins ...
          Channel Islander ...
would be turned into three rows:

    primary_ethnic_origin, secondary ethnic origin, tertiary   ethnic origin` ...
    European origins     , [empty]                 , [empty] ...
    European origins     , Channel Isles origins   , [empty] ...
    European origins     , Channel Isles origins   , Channel Islander ...
the sum of tertiary ethnic origins will not be the same as the total estimate for secondary ethnic origins, and the sum of all secondary ethnic origins will not equate to the total of the primary ethnic origins.

### `census.csv`
- **area_code** the first three symbols of the postal code
- **primary_ethnic_origin** the broadest ethnic region the row corresponds to
- **secondary_ethnic_origin** the secondary (more specific) region the row corresponds to
- **tertiary_ethnic_origin** the most specific ethnic group the row corresponds to 
- **total_count** the total number of individuals who marked this
- **male_count** the total number of self-described males
- **female_count** the total number of self-described females
 

## Ottowa covid neighbourhood infection rates
**location**: `cleaned_data_sets/ottowa_covid/statistics`

Cumulative and monthly counts and rates of confirmed COVID-19 in Ottawa neighbourhoods between July 2020 and April 2021, excluding cases linked to outbreaks in long-term care homes (LTCH) and retirement homes (RH). Data originally taken from Ottowa's open data initiative. https://open.ottawa.ca/datasets/ottawa::data-tables-for-ons-neighbourhood-covid-19-maps/about

### Extra Information
In addition to random rounding, area and data suppression has been adopted to further protect the confidentiality of individual respondents' personal information. Area and data suppression results in the deletion of all information for geographic areas with populations below a specified size with numeric values replaced with "Suppressed". Suppression of data can be due to poor data quality or to other technical reasons.

Additionally, rates or numbers of active cases at or below 5 will be be replaced with "<5"

### `cumulative_covid.csv`
- **neighbourhood** the name of the neighbourhood in Ottowa
- **cumulative_rate** Cumulative rate (per 100 000 population), excluding cases linked to outbreaks in LTCH and RH – cumulative number of residents with confirmed COVID-19 in a neighbourhood, excluding those linked to outbreaks in LTCH and RH, divided by the total population of that neighbourhood
- **cumulative_cases** Cumulative number of cases, excluding cases linked to outbreaks in LTCH and RH - cumulative number of residents with confirmed COVID-19 in a neighbourhood, excluding cases linked to outbreaks in LTCH and RH
- **estimated_total_population** estimated population of each neighbourhood

### `monthly_covid.csv`
neighbourhood,date,monthly rate (per 100k),number of active cases

- **neighbourhood** the name of the neighbourhood in ottowa
- **date** the date, in the format "[full month name] [year]"
- **monthly_rate** Cumulative rate (per 100 000 population), excluding cases linked to outbreaks in LTCH and RH – cumulative number of residents with confirmed COVID-19 in a neighbourhood, excluding those linked to outbreaks in LTCH and RH, divided by the total population of that neighbourhood
- **number_active_cases** Cumulative number of cases, excluding cases linked to outbreaks in LTCH and RH - cumulative number of residents with confirmed COVID-19 in a neighbourhood, excluding cases linked to outbreaks in LTCH and RH

## Neighbourhood postal codes
**location** `cleaned_data/ottowa neighbourhood zip codes.csv`
contains a mapping between postal code and ottowa neighbourhood. Google maps was used to determine postal code of each neighbourhood.

- **postal_area** the first three letters of the postal code the neighbourhood resides in
- **full_postal_code** the full six letter of the postal code the neighbourhood resides in
- **neighbourhood_name** the full name of the ottowa neighbourhood


