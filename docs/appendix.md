# Appendix





## Constructed variables

### Identifying partners {#partners}

Variable: __parnter__
location: clean/....

There are some discrepancies in the data when finding consistent partner matches to unique individuals across the multiple data sets. 

We can find partner data in two of the datasets: __partners_rtb__ and __samh__. In the __partners_rtb__ dataset, we have three variables for every lopnr-year observation:

*	Lopnrsamh – (no definition given in the excel sheet) 1987-1997.
*	Lopnrsambo – “sambo’s personummer” from 1998.
*	Lopnrmakpart – “make/maka/partners personummer” ( I believe this is technically married) from 1998.

From the __samh__ dataset, we have one variable:
*	LopNrSamh – (no definition given in the accompanying excel sheet).

Since no particular partner variable was consistent over time, a new varaible is created, “partner”,  that takes the value of whichever variable has valid data (of one of the above variables) for that lopnr/year.  If there are two values, the priority is for the lopnrsamh from the __partners_rtb__ dataset (it seems to have the best coverage).  

A screenshot for an particular individual with multiple partners over time to illustrate.

<img src="figures/partners_png.PNG" width="100%" />


### Identifying change in kommun

Variable: __change_kommun__
location: clean/....

In the same fashion as identifying the change in a housing over time for an individual, we can observe when an individual has relocated outside of a geographical area when the geographical indicator changes. Variables may then be created to capture this trend.

### Identifying household size

Variable: __household_size__
location: clean/....

As size of household is not present in the data (number of individuals inhabiting a particular residence),
and estimate is constructed by the following combination of data items.
First, total number of children living at the residence is calculated by summing the items: barn_0_3, barn_4_6,barn_7_10_barn_11_15, and barn_16_17.
This estimate is augmented by 1 in the case of an individual living without a partner (no partner data available), or by 2 if a partner is living with that individual.
For example, an individual who has 2 children and living with a partner would have an calculated household size of 4 (2 children + 1 partner + 1 self)


### Identifying special housing

Variable: __special_housing__
location:

A particular housing situation in the context of healthy aging is that of special housing, taken to be composed predominantly of care home type housing options.
This attention has warranted a deeper look at how we can accurately identify whether or not an individual resides in a special housing. These are the considerations:

- Special housing may have entries in either the __municipal registers__ or the __Fastigehtsregister__.
- In the __municiple register__ we identify special housing when the variable __sbo__ is equal to __1__, or when the variable __boskat__ is equal to __2__.  We create a new variable, __special_housing__, when either one of these conditions are true.
- In the __Fastigehtsregister__ we identify special housing when the variable __scb_boskat__ is equal to __1__.


We can examine some cross tabulations of our new __special_housing__ variable ( from the municiple register) and the __scb_bostkat__ variable from Fastigehtsregister (which takes on the value of 1 when special housing)

<img src="figures/special_housing.png" width="100%" />
