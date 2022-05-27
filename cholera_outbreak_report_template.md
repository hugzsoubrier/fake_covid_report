---
title: "Cholera outbreak report"
output: 
  word_document:
    keep_md: true
---

# Introduction to this template

This is a template which can be used to create an automated outbreak situation
report for cholera. 

- It is organised by time, place and person. 
For a more detailed explanation of this template, please visit https://r4epis.netlify.com/outbreaks
- Feedback and suggestions are welcome at the [GitHub issues page](https://github.com/R4EPI/sitrep/issues)
- Text within <! > will not show in your final document. These comments are used
to explain the template. You can delete them if you want.

<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This comment will not show up when you knit the document.

A comment with a title with slashes indicates a name of a code chunk.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->


## Installing and loading required packages 
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// setup \\\
--------------------------------------------------------------------------------

Several packages are required for different aspects of  analysis with *R*. 
You will need to install these before starting. 

These packages can be quite large and may take a while to download in the
field. If you have access to a USB key with these packages, it makes sense to
copy and paste the packages into your computer's R package library 
(run the command .libPaths() to see the folder path). 

For help installing packages, please visit https://r4epis.netlify.com/welcome
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// define_current_week \\\
--------------------------------------------------------------------------------

You need to set the week you want to report on. Generally, this is the previous
week. Put it below.

aweek::set_week_start will define the beginning of the week. The standard is
Monday.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// read_fake_data \\\
--------------------------------------------------------------------------------


To play with this template, you can create fake data. Comment out this chunk
when you are using real data.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->


<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
You should load your data as a linelist, where each row is one case.

There are two options:
- Your data is from DHIS2: use read_DHIS_excel_data
- Your data is NOT FROM DHIS2 and in Excel, CSV, or Stata format: 
use read_nonDHIS_data
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// read_DHIS_data \\\
--------------------------------------------------------------------------------

This section is for data from DHIS2.
It uses the standardized MSF data dictionary.
If you didn't use the standardized data dictionary, go to read_nonDHIS_data.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->





<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// prep_DHIS_data \\\
--------------------------------------------------------------------------------

This section is for data from DHIS2 that you loaded in read_DHIS_data.

If you didn't use DHIS2 data, go to read_nonDHIS_data.

This step shows you the data dictionary. The data dictionary has variable names
in the data_element_shortname column. Possible values for each variable are
specified in code and name columns. Code has the shortened value and Name has
the full-text value.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->





<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// read_nonDHIS_data \\\
--------------------------------------------------------------------------------

This section is for data not from DHIS2.
If you have already loaded data from DHIS2, go to read_population_data.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->





<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// prep_nonDHIS_data \\\
--------------------------------------------------------------------------------

This section is for data not from DHIS2. 
If you have already loaded data from DHIS2, go to read_population_data.

It is more difficult to prepare the nonDHIS data. You can do it! It will just
take a little more work.

Checklist to update this script to match your data:
[ ] Comment out all lines in read_DHIS_data and prep_DHIS_data
[ ] Recode your variable names to match the dictionary
[ ] Recode variable contents to match the dictionary


This step shows you the data dictionary. The data dictionary has variable names
in the data_element_shortname column. Possible values for each variable are
specified in code and name columns. Code has the shortened value and Name has
the full-text value.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->






<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// read_population_data \\\
--------------------------------------------------------------------------------

This template uses population data to calculate things like incidence.

There are three options:
- You can read in a spreadsheet with age group and region data.
- You can put in the specific populations into the gen_population function. 
- If you have the total or regional populations, you can estimate the age group
from proportions.

Comment out the options you are not using.


Age group proportions are from the OCBA population denominators tool v1. The
proportions below are for sub-Saharan Africa in 2019. They are only an estimate!
If you have more specific proportions, you can use them below.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->






<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// lab_data \\\
--------------------------------------------------------------------------------

If you have lab data, you can read it in here.
You will need to make sure that your identifier (e.g. case_number) matches the
linelist.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// browse_data \\\
--------------------------------------------------------------------------------

You'll want to look at your data. Here are a few ways you can explore.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->





<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// remove_unused_data \\\
--------------------------------------------------------------------------------

Your data might have empty rows or columns you want to remove.
You can also use this section to create temporary datasets so you can review
specific variables or rows.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This part of the script will create and clean variables in your data.

All your cleaning and variable creation should happen in these chunks.
That way, in case something goes wrong, you can push the small arrow at the top
of the chunk to re-run all the code chunks up to the current one.

The chunks are:
- standardise_dates -- will set up and clean dates.
- create_age_group  -- creates the age group variables from age
- create_vars       -- creates variables based on other variables
- factor_vars       -- helps clean factor variables
- vector_vars       -- creates groups of variables for easy use


You must adapt this section according to your data!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->


<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// standardise_dates \\\
--------------------------------------------------------------------------------

This chunk will help you set up and clean your date variables.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// create_age_group \\\ 
--------------------------------------------------------------------------------

This chunk will help you set up your age group variable.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// create_vars \\\
--------------------------------------------------------------------------------

This chunk will help you construct new variables from other variables. It
includes numeric, factor, and character vectors.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

  


<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// factor_vars \\\
--------------------------------------------------------------------------------

This chunk will help you clean factor variables.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// vector_vars \\\
--------------------------------------------------------------------------------

This chunk creates groups of variables that you might want to use together. That
way, if you want to run the same function over these variables, you can run it
all at once. For example, you may want to look at frequency of all symptoms at
the same time.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// report_setup \\\
--------------------------------------------------------------------------------

This chunk removes cases after your reporting week and defines the start and end
of the reporting period.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// save_cleaned_data \\\
--------------------------------------------------------------------------------

You can save your cleaned dataset as an Excel. 
This automatically names your file "linelist_cleaned_DATE", where DATE is the
current date.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->







<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
After adjusting and running the above code, you will have a clean dataset.
This marks the start of the ANALYSIS portion of the template.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->



### Person
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This section focuses on who is affected - total, by sex, by age.
There is code to include:
- A bar chart of case numbers of incidence by age group.
- Attack rate (AR)
- Number of deaths (in suspected and confirmed cases)
- Mortality rates
- Case fatality ratio (CFR)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->



From the start of the outbreak up until 2019-W25 there were a 
total of 300 cases. There were
90 (30.0%) females and
115 (38.3%) males. 

The most affected age group was 45+ years. 



#### Demographics 

Cases by age group and definition 
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_age_group_and_def \\\
--------------------------------------------------------------------------------

This chunk will create a table of cases by age group and case definition.
You can only use this chunk if you have lab results and have defined a case
definition variable.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Age group | Confirmed cases (n)|     %| Probable cases (n)|     %| Suspected cases (n)|     %| Total|
|:---------|-------------------:|-----:|------------------:|-----:|-------------------:|-----:|-----:|
|0-2       |                   5|   2.2|                  1|   2.9|                   1|   2.7|     7|
|3-14      |                  18|   7.9|                  6|  17.1|                   2|   5.4|    26|
|15-29     |                  32|  14.0|                  4|  11.4|                   5|  13.5|    41|
|30-44     |                  38|  16.7|                  5|  14.3|                   4|  10.8|    47|
|45+       |                 135|  59.2|                 19|  54.3|                  25|  67.6|   179|
|Total     |                 228| 100.0|                 35| 100.0|                  37| 100.0|   300|



There were 95 (31.7%) cases missing information on sex and 0 (0.0%) missing age group.


Cases by age group and sex
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_age_group_and_sex \\\
--------------------------------------------------------------------------------

This chunk will create a table of cases by age group and sex.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Age group | Male cases (n)|     %| Female cases (n)|     %| Missing cases (n)|     %| Total|
|:---------|--------------:|-----:|----------------:|-----:|-----------------:|-----:|-----:|
|0-2       |              3|   2.6|                2|   2.2|                 2|   2.1|     7|
|3-14      |             12|  10.4|                7|   7.8|                 7|   7.4|    26|
|15-29     |             20|  17.4|               10|  11.1|                11|  11.6|    41|
|30-44     |             20|  17.4|               11|  12.2|                16|  16.8|    47|
|45+       |             60|  52.2|               60|  66.7|                59|  62.1|   179|
|Total     |            115| 100.0|               90| 100.0|                95| 100.0|   300|



Cases by population proportion (age group and sex)
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// total_props_agegroup_sex \\\
--------------------------------------------------------------------------------

You can also show cases by proportion of the total population by sex and age.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Age group | Male cases (n)|    %| Female cases (n)|    %| Missing cases (n)|    %| Total|
|:---------|--------------:|----:|----------------:|----:|-----------------:|----:|-----:|
|0-2       |              3|  1.0|                2|  0.7|                 2|  0.7|     7|
|3-14      |             12|  4.0|                7|  2.3|                 7|  2.3|    26|
|15-29     |             20|  6.7|               10|  3.3|                11|  3.7|    41|
|30-44     |             20|  6.7|               11|  3.7|                16|  5.3|    47|
|45+       |             60| 20.0|               60| 20.0|                59| 19.7|   179|
|Total     |            115| 38.3|               90| 30.0|                95| 31.7|   300|


Age pyramid
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// age_pyramid \\\
--------------------------------------------------------------------------------

This chunk creates an age/sex pyramid of your cases.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
![](cholera_outbreak_report_template_files/figure-docx/age_pyramid-1.png)<!-- -->



Of the patients, 92 (30.7%) were seen as outpatients and 208 (69.3%) were inpatients. Among inpatients, the median number of days admitted was 20, 
with a range between 1 and 113 days. 

From the start of the outbreak, 63 (21.0%) patients recevied treatment plan
A, 51 (17.0%)
received treatment plan B, and 50 (16.7%) received treatment plan C.



Cases by treatment plan and case definition
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_treatment_plan_case_def \\\
--------------------------------------------------------------------------------

This chunk creates a table of fluids treatment plan by case definition.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Fluid treatment plan | Confirmed cases (n)|     %| Probable cases (n)|     %| Suspected cases (n)|     %| Total|
|:--------------------|-------------------:|-----:|------------------:|-----:|-------------------:|-----:|-----:|
|None                 |                  47|  20.6|                  6|  17.1|                  11|  29.7|    64|
|Treatment plan A     |                  45|  19.7|                 12|  34.3|                   6|  16.2|    63|
|Treatment plan B     |                  42|  18.4|                  4|  11.4|                   5|  13.5|    51|
|Treatment plan C     |                  39|  17.1|                  5|  14.3|                   6|  16.2|    50|
|Unknown              |                  55|  24.1|                  8|  22.9|                   9|  24.3|    72|
|Total                |                 228| 100.0|                 35| 100.0|                  37| 100.0|   300|


The median number of days admitted was 20, 
with a range between 1 and 113 days. 
A total of 102 (34.0%) patients were readmitted to the CTC. 



Cases by dehydration severity at admission
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_illness_severity_admission \\\
--------------------------------------------------------------------------------

This chunk creates a table describing the dehydration level at admission.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Dehydration severity | Cases (n)|     %|
|:--------------------|---------:|-----:|
|Severe               |        70|  23.3|
|Some                 |        68|  22.7|
|None                 |        80|  26.7|
|Unknown              |        82|  27.3|
|Total                |       300| 100.0|



Cases by dehydration severity during stay 
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_illness_severity_stay \\\
--------------------------------------------------------------------------------

This chunk creates a table describing the dehydration level during the stay.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Dehydration severity | Cases (n)|     %|
|:--------------------|---------:|-----:|
|Severe               |        74|  24.7|
|Some                 |        75|  25.0|
|None                 |        85|  28.3|
|Unknown              |        66|  22.0|
|Total                |       300| 100.0|



Cases by lab results 
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_labs \\\
--------------------------------------------------------------------------------


This chunk gives the counts and proportions for all of the variables in LABS.
If you do not have lab results, comment out this chunk.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

```
## Note: Using an external vector in selections is ambiguous.
## ℹ Use `all_of(LABS)` instead of `LABS` to silence this message.
## ℹ See <https://tidyselect.r-lib.org/reference/faq-external-vector.html>.
## This message is displayed once per session.
```



|Results              | Culture (n)|     %| PCR (n)|     %| RDT (n)|     %|
|:--------------------|-----------:|-----:|-------:|-----:|-------:|-----:|
|Not done             |          50|  16.7|      38|  12.7|      52|  17.3|
|Negative             |          55|  18.3|      50|  16.7|      43|  14.3|
|Positive O1          |          45|  15.0|      47|  15.7|      48|  16.0|
|Positive O139        |          42|  14.0|      57|  19.0|      59|  19.7|
|Positive O1 & O139   |          57|  19.0|      59|  19.7|      53|  17.7|
|Invalid/contaminated |          51|  17.0|      49|  16.3|      45|  15.0|
|Total                |         300| 100.0|     300| 100.0|     300| 100.0|



Cases by vaccination status
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_vaccination_status \\\
--------------------------------------------------------------------------------

This chunk creates a table of the vaccination status of your cases.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Vaccination status         | Cases (n)|     %|
|:--------------------------|---------:|-----:|
|Yes - vaccination card/ink |        62|  20.7|
|Yes - verbal               |        92|  30.7|
|No                         |        73|  24.3|
|Unsure                     |        73|  24.3|
|Total                      |       300| 100.0|


#### Case fatality ratio 

Of 208 (69.3%) inpatients, there have been 62 (20.7%) deaths, of which 
42 (14.0%) 
were dead on arrival. 

Among inpatients who died, the time to death is shown below. 
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_time_to_death \\\
--------------------------------------------------------------------------------

If you have the time_to_death available, you can use this chunk to describe when
inpatients died. If not, comment it out.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Time (hours) | Deaths (n)|     %|
|:------------|----------:|-----:|
|0-4 hours    |         16|  25.8|
|>4-24 hours  |         15|  24.2|
|>24-48 hours |         17|  27.4|
|>48 hours    |         14|  22.6|
|Total        |         62| 100.0|



The case fatality ratio among inpatients with known outcomes is below.
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// overall_cfr \\\
--------------------------------------------------------------------------------

This chunk gives the case fatality ratio among inpatients with outcomes.
If you have no deaths reported, the table will not be useful.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

| Deaths| Cases| CFR (%)|95%CI          |
|------:|-----:|-------:|:--------------|
|     62|   208|    29.8|(24.00--36.34) |


The case fatality ratio by sex among inpatients with known outcomes is below. 
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// cfr_by_sex \\\
--------------------------------------------------------------------------------

This chunk gives the case fatality ratio among inpatients with outcomes, divided
by sex. If you have no deaths reported, the table will not be useful.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Sex    | Deaths| Cases| CFR (%)|95%CI          |
|:------|------:|-----:|-------:|:--------------|
|Male   |     25|    85|    29.4|(20.79--39.82) |
|Female |     19|    60|    31.7|(21.31--44.23) |
|-      |     18|    63|    28.6|(18.90--40.70) |
|Total  |     62|   208|    29.8|(24.00--36.34) |



CFR by age group among inpatients with known outcomes
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// cfr_by_age_group \\\
--------------------------------------------------------------------------------

This chunk gives the case fatality ratio among inpatients with outcomes, divided
by age group. If you have no deaths reported, the table will not be useful.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Age group | Deaths| Cases| CFR (%)|95%CI          |
|:---------|------:|-----:|-------:|:--------------|
|0-2       |      1|     5|    20.0|(3.62--62.45)  |
|3-14      |      4|    15|    26.7|(10.90--51.95) |
|15-29     |     12|    35|    34.3|(20.83--50.85) |
|30-44     |      9|    35|    25.7|(14.16--42.07) |
|45+       |     36|   118|    30.5|(22.92--39.32) |
|Total     |     62|   208|    29.8|(24.00--36.34) |


<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// cfr_by_case_def \\\
--------------------------------------------------------------------------------

This chunk gives the case fatality ratio among inpatients with outcomes, divided
by case definition. You must have a case definition defined to use this. If you
have no deaths, the table will not be useful.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




#### Attack rate

The attack rate per 10,000 population is below (based on available population data available for the catchment area/region of interest). 



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// collect_variables \\\
--------------------------------------------------------------------------------

This defines your population by summing up the population by age group.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




Below gives the attack rate per 10,000 population (N = 4,999.5)

<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
///attack_rate \\\
--------------------------------------------------------------------------------

This chunk calculates the attack rate and then shows you the confidence
intervals.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

| Cases (n)| AR (per 10,000)|            95%CI|
|---------:|---------------:|----------------:|
|       300|           600.1| (537.54--669.33)|

Here, we can see that the attack rate for a population of 4,999.5 was 600.06 (CI 537.54--669.33).

To give attack rate by age group, with appropriate population denominators, use the following code. 



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// attack_rate_by_agegroup \\\
--------------------------------------------------------------------------------

This chunk calculates the attack rate by age group and then gives a table of
attack rate by group.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

|Age group | Cases (n)| Population| AR (per 10,000)|95%CI              |
|:---------|---------:|----------:|---------------:|:------------------|
|0-2       |         7|      340.0|           205.9|(100.08--418.81)   |
|3-14      |        26|    1,811.0|           143.6|(98.16--209.53)    |
|15-29     |        41|    1,380.0|           297.1|(219.75--400.56)   |
|30-44     |        47|      808.0|           581.7|(440.23--764.95)   |
|45+       |       179|      660.5|         2,710.1|(2385.06--3061.56) |



#### Mortality attributable to cholera
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This section can only be used if you are in a closed population (eg refugee
camp). The assumptions don't hold in an open/community setting.

This chunk calculates the attack rate by age group and then gives a table of
attack rate by group.

This section gives mortality rates attributable to cholera in a closed
population. It does not calculate all-cause mortality. It assumes that all
cholera deaths are among inpatients.

This demonstrates three ways of calculating mortality rate based on catchment
population (twice) and based on hospital population.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// collect_variables_rates \\\
--------------------------------------------------------------------------------

This chunk calculates key variables to do mortality rate.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// mortality_rate \\\
--------------------------------------------------------------------------------

To produce a mortality rate (attribuatble to cholera) per 10,000 people use
the following code chunk. This assumes that you are capturing every cholera
death in your population.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Mortality rate attributable to cholera per 10,000 population


| Deaths| Population| Mortality (per 10,000)|95%CI            |
|------:|----------:|----------------------:|:----------------|
|     97|     4999.5|                    194|(159.31--236.11) |



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// mortality_rate_CMR \\\
--------------------------------------------------------------------------------

To produce a crude mortality rate attributable to cholera per 10,000 people per 
day, use the folowing code chunk. 

This assumes that you are capturing every cholera death in your population and 
that your population remains stable over the time period of interest. 

In this situation the time period of interest is from the beginning of the 
epiweek your first case occured in, until the last day of the epiweek you are 
currently reporting on. (see this presentation (https://www.odi.org/sites/odi.org.uk/files/odi-assets/events-presentations/776.pdf) for more detail)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Crude mortality rate attributable to cholera per 10,000 population per day


| Deaths| Person-days| Mortality (per 10,000/day)|95%CI        |
|------:|-----------:|--------------------------:|:------------|
|     97|     2619738|                        0.4|(0.30--0.45) |



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// mortality_rate_patients \\\
--------------------------------------------------------------------------------

Alternatively, if you are unsure whether your hospital deaths are
representative of the wider population, use the following code chunk. 
This uses the person days of cases in your linelist with a known outcome. 
However, this will give you an unreasonably high mortality rate, as 
those in hospital will only be the most severely affected. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Mortality rate attributable to cholera per 10,000 patients per day


| Deaths| Population| Mortality (per 10,000/day)|95%CI           |
|------:|----------:|--------------------------:|:---------------|
|     97|       8742|                        111|(91.05--135.16) |

### Time
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This section focuses on the when of the outbreak:
- When did cases fall ill?
- Are numbers increasing or decreasing?

There is code to include an epi curve.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

There were 0 (0.0%) cases missing dates of onset.

<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// epicurve \\\
--------------------------------------------------------------------------------

# This chunk will calculate weekly incidence and plot your epicurve.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

```
## Warning: It is deprecated to specify `guide = FALSE` to remove a guide. Please
## use `guide = "none"` instead.
```

![](cholera_outbreak_report_template_files/figure-docx/epicurve-1.png)<!-- -->

The peak of the outbreak was in 2018-W15.



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// biweekly_epicurve \\\
--------------------------------------------------------------------------------

If needed, you can plot a biweekly epicurve. You can also do this by month,
quarter, or year. You can change the start of your week as needed.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->


```
## Warning: It is deprecated to specify `guide = FALSE` to remove a guide. Please
## use `guide = "none"` instead.
```

![](cholera_outbreak_report_template_files/figure-docx/biweekly_epicurve-1.png)<!-- -->



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// incidence_by_gender \\\
--------------------------------------------------------------------------------

You can plot weekly incidence by gender using this chunk.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->

![](cholera_outbreak_report_template_files/figure-docx/incidence_by_gender-1.png)<!-- -->



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// incidence_by_case_def \\\
--------------------------------------------------------------------------------

This chunk shows the weekly incidence by case definition. You must have a
defined case definition variable.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
![](cholera_outbreak_report_template_files/figure-docx/incidence_by_case_def-1.png)<!-- -->



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// incidence_by_sex_facility \\\
--------------------------------------------------------------------------------

This chunk limits the data to only inpatients, then stratifies by sex.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Cases by week of onset among inpatients by sex 
![](cholera_outbreak_report_template_files/figure-docx/incidence_by_sex_facility-1.png)<!-- -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// attack_rate_per_week \\\
--------------------------------------------------------------------------------

This chunk creates a table of attack rate by week
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Attack rate per 10,000 population by week 


|  Epiweek| Cases (n)| Population| AR (per 10,000)|          95%CI|
|--------:|---------:|----------:|---------------:|--------------:|
| 2018-W03|         2|     4999.5|               4|  (1.10--14.58)|
| 2018-W04|         3|     4999.5|               6|  (2.04--17.63)|
| 2018-W05|         7|     4999.5|              14|  (6.78--28.88)|
| 2018-W06|        12|     4999.5|              24| (13.74--41.91)|
| 2018-W07|        14|     4999.5|              28| (16.69--46.95)|
| 2018-W08|         3|     4999.5|               6|  (2.04--17.63)|
| 2018-W09|        21|     4999.5|              42| (27.49--64.13)|
| 2018-W10|        13|     4999.5|              26| (15.20--44.44)|
| 2018-W11|        14|     4999.5|              28| (16.69--46.95)|
| 2018-W12|        22|     4999.5|              44| (29.08--66.54)|
| 2018-W13|        30|     4999.5|              60| (42.07--85.53)|
| 2018-W14|        21|     4999.5|              42| (27.49--64.13)|
| 2018-W15|        31|     4999.5|              62| (43.72--87.88)|
| 2018-W16|        31|     4999.5|              62| (43.72--87.88)|
| 2018-W17|        25|     4999.5|              50| (33.89--73.72)|
| 2018-W18|        19|     4999.5|              38| (24.34--59.28)|
| 2018-W19|        14|     4999.5|              28| (16.69--46.95)|
| 2018-W20|        18|     4999.5|              36| (22.79--56.84)|
 


<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// cumulative_attack_rate_per_week \\\
--------------------------------------------------------------------------------

This chunk calculates the cumulative attack rate per week.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Cumulative attack rate per 10,000 population per week


|  Epiweek| Cases (n)| Population| AR (per 10,000)|            95%CI|
|--------:|---------:|----------:|---------------:|----------------:|
| 2018-W03|         2|     4999.5|             4.0|    (1.10--14.58)|
| 2018-W04|         5|     4999.5|            10.0|    (4.27--23.39)|
| 2018-W05|        12|     4999.5|            24.0|   (13.74--41.91)|
| 2018-W06|        24|     4999.5|            48.0|   (32.28--71.33)|
| 2018-W07|        38|     4999.5|            76.0|  (55.43--104.15)|
| 2018-W08|        41|     4999.5|            82.0|  (60.51--111.06)|
| 2018-W09|        62|     4999.5|           124.0|  (96.86--158.65)|
| 2018-W10|        75|     4999.5|           150.0| (119.85--187.63)|
| 2018-W11|        89|     4999.5|           178.0| (144.89--218.55)|
| 2018-W12|       111|     4999.5|           222.0| (184.70--266.68)|
| 2018-W13|       141|     4999.5|           282.0| (239.64--331.67)|
| 2018-W14|       162|     4999.5|           324.0| (278.43--376.82)|
| 2018-W15|       193|     4999.5|           386.0| (336.08--443.08)|
| 2018-W16|       224|     4999.5|           448.0| (394.11--508.97)|
| 2018-W17|       249|     4999.5|           498.0| (441.13--561.88)|
| 2018-W18|       268|     4999.5|           536.1| (476.98--601.99)|
| 2018-W19|       282|     4999.5|           564.1| (503.45--631.48)|
| 2018-W20|       300|     4999.5|           600.1| (537.54--669.33)|



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// cumulative_attack_rate_per_week \\\
--------------------------------------------------------------------------------

This chunk calculates the CFR among inpatients as a proportion per week.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Case fatality ratio as a proportion among inpatients by week


|  Epiweek| Deaths| Cases| CFR (%)|          95%CI|
|--------:|------:|-----:|-------:|--------------:|
| 2018-W03|      1|     2|    50.0|  (9.45--90.55)|
| 2018-W04|      1|     2|    50.0|  (9.45--90.55)|
| 2018-W05|      3|     6|    50.0| (18.76--81.24)|
| 2018-W06|      1|     8|    12.5|  (2.24--47.09)|
| 2018-W07|      3|     7|    42.9| (15.82--74.95)|
| 2018-W08|      0|     3|     0.0|  (0.00--56.15)|
| 2018-W09|      4|    13|    30.8| (12.68--57.63)|
| 2018-W10|      0|     4|     0.0|  (0.00--48.99)|
| 2018-W11|      5|    10|    50.0| (23.66--76.34)|
| 2018-W12|      7|    16|    43.8| (23.10--66.82)|
| 2018-W13|      3|    20|    15.0|  (5.24--36.04)|
| 2018-W14|      5|    18|    27.8| (12.50--50.87)|
| 2018-W15|      8|    23|    34.8| (18.81--55.11)|
| 2018-W16|      4|    22|    18.2|  (7.31--38.52)|
| 2018-W17|      8|    21|    38.1| (20.75--59.12)|
| 2018-W18|      3|    11|    27.3|  (9.75--56.56)|
| 2018-W19|      3|    10|    30.0| (10.78--60.32)|
| 2018-W20|      3|    12|    25.0|  (8.89--53.23)|



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
You could plot the AR (in the population) and CFR (among inpatients only)
together with the epicurve by epiweek.

We will do this in three steps: 
- creating the AR graph (ar_line_graph)
- creating the CFR graph (cfr_line_graph)
- combining and plotting (epicurve_ar_cfr)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->


<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// ar_line_graph \\\
--------------------------------------------------------------------------------

This chunk sets up the AR graph. (It does not print the graph automatically.)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// cfr_line_graph \\\
--------------------------------------------------------------------------------

This chunk sets up the CFR graph. (It does not print the graph automatically.)
If you do not have any deaths in your data set, this will not show anything.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// epicurve_ar_cfr \\\
--------------------------------------------------------------------------------

This chunk prints the AR and CFR with the epicurve.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
![](cholera_outbreak_report_template_files/figure-docx/epicurve_ar_cfr-1.png)<!-- -->



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_admissions_by_epiweek \\\
--------------------------------------------------------------------------------

This chunk creates a table showing inpatient admissions by epiweek.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Inpatient admissions by case definition and week  


|value    | Confirmed (n)|     %| Probable (n)|   %| Suspected (n)|     %| Total|
|:--------|-------------:|-----:|------------:|---:|-------------:|-----:|-----:|
|2018-W03 |             1|   0.6|            0|   0|             1|   4.2|     2|
|2018-W04 |             2|   1.3|            0|   0|             0|   0.0|     2|
|2018-W05 |             4|   2.5|            1|   4|             1|   4.2|     6|
|2018-W06 |             5|   3.1|            3|  12|             0|   0.0|     8|
|2018-W07 |             6|   3.8|            1|   4|             0|   0.0|     7|
|2018-W08 |             3|   1.9|            0|   0|             0|   0.0|     3|
|2018-W09 |            12|   7.5|            1|   4|             0|   0.0|    13|
|2018-W10 |             2|   1.3|            1|   4|             1|   4.2|     4|
|2018-W11 |             7|   4.4|            1|   4|             2|   8.3|    10|
|2018-W12 |            11|   6.9|            4|  16|             1|   4.2|    16|
|2018-W13 |            14|   8.8|            2|   8|             4|  16.7|    20|
|2018-W14 |            12|   7.5|            2|   8|             4|  16.7|    18|
|2018-W15 |            19|  11.9|            2|   8|             2|   8.3|    23|
|2018-W16 |            19|  11.9|            1|   4|             2|   8.3|    22|
|2018-W17 |            19|  11.9|            1|   4|             1|   4.2|    21|
|2018-W18 |             7|   4.4|            3|  12|             1|   4.2|    11|
|2018-W19 |             7|   4.4|            1|   4|             2|   8.3|    10|
|2018-W20 |             9|   5.7|            1|   4|             2|   8.3|    12|
|Total    |           159| 100.0|           25| 100|            24| 100.0|   208|



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_admissions_by_epiweek \\\
--------------------------------------------------------------------------------

This chunk creates a table showing inpatient exits by type per epiweek.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Inpatient discharges by reason for exit and week 


|Week     | Died (n)|     %| Discharged (n)|     %| Left (n)|     %| Transferred (n)|     %| Total|
|:--------|--------:|-----:|--------------:|-----:|--------:|-----:|---------------:|-----:|-----:|
|2018-W03 |        1|   1.6|              0|   0.0|        1|   2.6|               0|   0.0|     2|
|2018-W04 |        1|   1.6|              1|   3.0|        0|   0.0|               0|   0.0|     2|
|2018-W05 |        3|   4.8|              0|   0.0|        2|   5.3|               1|   1.3|     6|
|2018-W06 |        1|   1.6|              1|   3.0|        0|   0.0|               6|   8.0|     8|
|2018-W07 |        3|   4.8|              0|   0.0|        1|   2.6|               3|   4.0|     7|
|2018-W08 |        0|   0.0|              0|   0.0|        1|   2.6|               2|   2.7|     3|
|2018-W09 |        4|   6.5|              3|   9.1|        3|   7.9|               3|   4.0|    13|
|2018-W10 |        0|   0.0|              1|   3.0|        1|   2.6|               2|   2.7|     4|
|2018-W11 |        5|   8.1|              2|   6.1|        3|   7.9|               0|   0.0|    10|
|2018-W12 |        7|  11.3|              4|  12.1|        1|   2.6|               4|   5.3|    16|
|2018-W13 |        3|   4.8|              4|  12.1|        4|  10.5|               9|  12.0|    20|
|2018-W14 |        5|   8.1|              2|   6.1|        4|  10.5|               7|   9.3|    18|
|2018-W15 |        8|  12.9|              3|   9.1|        4|  10.5|               8|  10.7|    23|
|2018-W16 |        4|   6.5|              4|  12.1|        5|  13.2|               9|  12.0|    22|
|2018-W17 |        8|  12.9|              3|   9.1|        3|   7.9|               7|   9.3|    21|
|2018-W18 |        3|   4.8|              2|   6.1|        1|   2.6|               5|   6.7|    11|
|2018-W19 |        3|   4.8|              2|   6.1|        1|   2.6|               4|   5.3|    10|
|2018-W20 |        3|   4.8|              1|   3.0|        3|   7.9|               5|   6.7|    12|
|Total    |       62| 100.0|             33| 100.0|       38| 100.0|              75| 100.0|   208|






### Place 
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This section focuses on the where of the outbreak: what area is affected, how
many villages, and so on.

There is code to include maps based on distribution of cases. You must have a
shapefile to create this map.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->


#### Descriptive



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_region_facility \\\
--------------------------------------------------------------------------------

This chunk creates a basic table of the number and percent of cases by region
and by facility. If you only have one facility, you can remove the strata.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Cases by region and facility type


|Region    | Inpatient (n)|     %| Outpatient (n)|     %| Total|
|:---------|-------------:|-----:|--------------:|-----:|-----:|
|Village A |            60|  28.8|             19|  20.7|    79|
|Village B |            52|  25.0|             29|  31.5|    81|
|Village C |            42|  20.2|             20|  21.7|    62|
|Village D |            54|  26.0|             24|  26.1|    78|
|Total     |           208| 100.0|             92| 100.0|   300|



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// describe_by_region_outcome \\\
--------------------------------------------------------------------------------

This chunk creates a basic table of the outcomes among inpatients by region.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Inpatient discharges by reason for exit and region 


|Region    | Died (n)|     %| Discharged (n)|     %| Left (n)|     %| Transferred (n)|     %| Total|
|:---------|--------:|-----:|--------------:|-----:|--------:|-----:|---------------:|-----:|-----:|
|Village A |       18|  29.0|             11|  33.3|       11|  28.9|              20|  26.7|    60|
|Village B |       15|  24.2|              8|  24.2|        8|  21.1|              21|  28.0|    52|
|Village C |       11|  17.7|              5|  15.2|       11|  28.9|              15|  20.0|    42|
|Village D |       18|  29.0|              9|  27.3|        8|  21.1|              19|  25.3|    54|
|Total     |       62| 100.0|             33| 100.0|       38| 100.0|              75| 100.0|   208|



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// attack_rate_by_region \\\
--------------------------------------------------------------------------------

If you do not have a shapefile, you may want to calculate attack rates by
region.

Consider facet wrapping by a larger unit if you have many regions (eg if you
have patients from 10+ villages, you may want to show your tables by health
zone)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Attack rage per 10,000 population by region 


|    Region| Cases (n)| Population| AR (per 10,000)|             95%CI|
|---------:|---------:|----------:|---------------:|-----------------:|
| Village A|        79|      1,105|           714.9|  (577.40--882.15)|
| Village B|        81|        870|           931.0| (755.43--1142.41)|
| Village C|        62|      1,775|           349.3|  (273.43--445.25)|
| Village D|        78|      1,225|           636.7|  (513.18--787.57)|


<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// bar_attack_rate_by_region \\\
--------------------------------------------------------------------------------

You can then plot the above table on a bar plot. AR is on the y-axis, and it
will show regions in descending order by AR.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
![](cholera_outbreak_report_template_files/figure-docx/bar_attack_rate_by_region-1.png)<!-- -->



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// mortality_rate_region \\\
--------------------------------------------------------------------------------

You could also calculate mortality rate by region (check the mortality code
chunk in Person section for assumptions).
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
Mortality rate per 10,000 population by region 


|Region    | Deaths| Population| Mortality (per 10,000)|95%CI            |
|:---------|------:|----------:|----------------------:|:----------------|
|Village A |     24|       1105|                  217.2|(146.38--321.15) |
|Village B |     27|        870|                  310.3|(214.15--447.77) |
|Village C |     21|       1775|                  118.3|(77.51--180.19)  |
|Village D |     25|       1225|                  204.1|(138.61--299.54) |




#### Maps 
<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// read_shapefiles \\\
--------------------------------------------------------------------------------

To create maps, you need to have a shapefile of the area. Often, the MSF GIS
unit can provide shapefiles.

Your shapefile can be a polygon or points. Polygons do not need to be contiguous.

The names of the polygons or points MUST match the names in your linelist.

Your coordinate reference system needs to be WGS84.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// dot_map \\\
--------------------------------------------------------------------------------

If you have the coordinates for your cases, you can create a dot map showing
where the cases are.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->




<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// choropleth_maps \\\
--------------------------------------------------------------------------------

Once you have loaded your shapefile, you can map the case counts or attack rates.

You will want to make your counts or AR categorical. R will not do this
automatically (unlike QGIS or ArcGIS).

This chunk will walk you through several steps:
- Create table with categories of counts or ARs by region.
- Join your table with your shapefile.
- Choose which variable you will use.

Make sure you delete or comment out the section you are not using.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
![](cholera_outbreak_report_template_files/figure-docx/choropleth_maps-1.png)<!-- -->



<!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// map_for_loop_epiweek \\\
--------------------------------------------------------------------------------

This chunk will create a map and barplot by week.

You need to:
- Decide if you want to show counts, AR, or categories of counts/AR.
- Define categories for your variable.
- Replace `Cases (n)` and `AR (per 10,000)` or "categories", appropriately.


If you have a lot of map regions, you may want to use facet_wrap to show
sub-units.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ -->
![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-1.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-2.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-3.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-4.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-5.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-6.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-7.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-8.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-9.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-10.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-11.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-12.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-13.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-14.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-15.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-16.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-17.png)<!-- -->![](cholera_outbreak_report_template_files/figure-docx/map_for_loop_epiweek-18.png)<!-- -->

