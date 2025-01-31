# Data Integration and Linkage




## Overview

A large amount of data from the registrars is accessed through Statistics Sweden (SCB).  This data is delivered in text format (file extension .txt), and is partitioned, for the most part, into individual files separated by both year and grouped data set.  While the data contained in this data originates from the specified data Registrars previously outlined, the data is received from SCB consolidated and grouped into various data sets which require further cleaning and processing.  These grouped data sets are described below. 


### Dataset overview


Most of the descriptive data comes from LISA (lev_lisa in the table below), with more than 5 million individuals, over 128 million individual-year observations, and 95 variables across 30 years.  The coverage of the other data sets is also documented, with linking of data sets possible by matching on a individual's unique identifier, Lopnr.

<table class="table table-responsive table-hover" style="font-size: 11px; margin-left: auto; margin-right: auto;">
<caption style="font-size: initial !important;">(\#tab:unnamed-chunk-2)Dataset descriptions</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Dataset </th>
   <th style="text-align:left;"> First year </th>
   <th style="text-align:left;"> Last year </th>
   <th style="text-align:left;"> Obs </th>
   <th style="text-align:left;"> No. Variables </th>
   <th style="text-align:left;"> Unique ids </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> lev_civil </td>
   <td style="text-align:left;"> 1998 </td>
   <td style="text-align:left;"> 2019 </td>
   <td style="text-align:left;"> 1523503 </td>
   <td style="text-align:left;"> 6 </td>
   <td style="text-align:left;"> 1273606 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_fodelseland </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> 5687933 </td>
   <td style="text-align:left;"> 5 </td>
   <td style="text-align:left;"> 5687931 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_housing </td>
   <td style="text-align:left;"> 2012 </td>
   <td style="text-align:left;"> 2020 </td>
   <td style="text-align:left;"> 29628301 </td>
   <td style="text-align:left;"> 23 </td>
   <td style="text-align:left;"> 3691638 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_in_utv </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> 1199921 </td>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> 813991 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_ind_koord </td>
   <td style="text-align:left;"> 1990 </td>
   <td style="text-align:left;"> 2019 </td>
   <td style="text-align:left;"> 172620690 </td>
   <td style="text-align:left;"> 5 </td>
   <td style="text-align:left;"> 5713728 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_inr_flytt </td>
   <td style="text-align:left;"> 1998 </td>
   <td style="text-align:left;"> 2019 </td>
   <td style="text-align:left;"> 5794996 </td>
   <td style="text-align:left;"> 7 </td>
   <td style="text-align:left;"> 2649340 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_lisa </td>
   <td style="text-align:left;"> 1990 </td>
   <td style="text-align:left;"> 2019 </td>
   <td style="text-align:left;"> 128428907 </td>
   <td style="text-align:left;"> 95 </td>
   <td style="text-align:left;"> 5514771 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_partners_RTB </td>
   <td style="text-align:left;"> 1987 </td>
   <td style="text-align:left;"> 2019 </td>
   <td style="text-align:left;"> 134704934 </td>
   <td style="text-align:left;"> 5 </td>
   <td style="text-align:left;"> 5255938 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_population_personnr </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> 5754023 </td>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> 5713728 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_samh </td>
   <td style="text-align:left;"> 1987 </td>
   <td style="text-align:left;"> 2019 </td>
   <td style="text-align:left;"> 82660469 </td>
   <td style="text-align:left;"> 14 </td>
   <td style="text-align:left;"> 4071181 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lev_utb_foraldrar </td>
   <td style="text-align:left;"> 1990 </td>
   <td style="text-align:left;"> 2019 </td>
   <td style="text-align:left;"> 110702340 </td>
   <td style="text-align:left;"> 4 </td>
   <td style="text-align:left;"> 3690078 </td>
  </tr>
</tbody>
</table>

## Linkage Methodology

Each dataset includes unique personal identifiers that allow for accurate matching across registers. The primary identifier used for linkage is the **Personal Identity Number (PIN)**, assigned to each resident in Sweden. This identifier enables the seamless integration of information from different datasets, ensuring that all data points accurately correspond to the same individual.

### Steps in the Linkage Process

1. **Data Standardization**: Each dataset was reviewed to ensure consistent formatting of the PIN and other relevant variables used in the linkage process.
2. **Primary Linkage Using PIN**: The Personal Identity Number serves as the primary key for linking data across registers.
3. **Secondary Checks**: In cases where additional verification was required, variables like **birth date** and **sex** were used to confirm the linkage.

### Example Linkage

An example of the linkage process would involve connecting records from the **Total Population Register** and the **National Patient Register**. Using the PIN, we link demographic data (e.g., birth date, sex, migration details) with health data (e.g., diagnoses, treatments) for the same individual. This linkage enables us to analyze health outcomes in the context of demographic factors.



