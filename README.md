# CHE2410 - Analysis of Ground-Level 8-hr Ozone Concentrations Versus COVID-19 Death Rate by County in Indiana, Supplemented by Analysis of Presence of a Steel Mill Effects

Repository for all files and items in Project 1 of CHE 2410

## Background and Motivation for This Topic

High concentrations of ground-level ozone have been correlated with causing respiratory issues by the CDC (https://www.cdc.gov/air/ozone.html#:~:text=Ozone%20has%20also%20been%20linked,during%20exercise%20or%20outdoor%20activities). For my project, I wanted to capture that concept and test it with COVID-19 data to determine whether those in areas of high ozone pollution were more at risk from the virus.

My motivation for this analysis is rooted in my job at Bloom Engineering Comoany, Inc. in the South Hills here in Pittsburgh. Bloom is a manufacturer and consultent for combustion technology that is primarily used in the steel and aluminum manufacturing industries. My role there is within the R&D department, where we focus on developing low-NOx-emitting equipment for our customers. I am hoping to determine whether we at Bloom are indirectly responsible for lowering NOx production from steel mills and, therefore, lowering COVID risks for the counties that have a mill.

I had initially wanted to evaluate NOx how NOx concentrations affected COVID risks, but counties often do not have details regarding specific ground-level NOx concentrations. Ozone still is representative of NOx emissions because it is formed via chemical reactions between oxides of nitrogen and oxygen in the atmosphere. Therefore, for this project, I am operating under the assumption that the presence of ozone must be a result of a equitable presence of NOx. I decided to use the state of Indiana for this study because it has the highest number of steel mills and leads the US in steel production.

My topic for Project 1 will thus focus on evaluating COVID deaths per positive case by county in Indiana. The points of comparison will first be air quality as measured by PPM of ozone over an 8-hour basis for 2021 (the most recent data provided by the EPA). My second point of comparison will be whether having a steel mill in a given county raises the risk of COVID deaths per positive case. My hypothesis is that, since ozone pollution has been linked to respiratory issues, and since steel mills tend to output a fair amount of NOx/ozone pollution, counties with steel mills will have a higher death rate.

Counties that either had no ozone pollution data or no CVOID data available were excluded from the data sets that will be used for analysis.


## A Summary of my Results

### Initial Thoughts

I first decided to plot the death rate versus ozone levels for each county to get a feel for the data and to observe if there was an immediately recognizable correlation. Highlighted in yellow are counties that have a steel mill within them.

<p align="center">
  <img src="https://github.com/bcerminarache2410/CHE2410-Project-1/blob/main/deathrate%20vs%20ozone%20-%20with%20reg.png" width="350"><br>
  <img src="https://github.com/bcerminarache2410/CHE2410-Project-1/blob/main/death%20rate%20vs%20ozone%20-%20reg%20nums.png" width="500">
</p>

After utilizing Python's OLS linear regression model package, I was able to conclude that the P-values of the linearly-fit parameters prevented me from concluding that there was a significant correlation. Therefore, further analyses would need to be concluded.


### Analysis of Groups

The next step I took to determine any relationships was grouping the data in the form of no steel mill present versus at least one steel mill present.


Running a regression analysis on these grouped values with ozone pollution as the response variable produced the following results:

<p align="center">
  <img src="https://github.com/bcerminarache2410/CHE2410-Project-1/blob/main/mill%20presence%20vs%20ozone%20-%20with%20reg.png" width="350"><br>
  <img src="https://github.com/bcerminarache2410/CHE2410-Project-1/blob/main/mill%20presence%20vs%20ozone%20-%20reg%20nums.png" width="500">
</p>

The P-values of the parameters are less than 0.05, which allow me to assume that there is a significant linear relationship present for these variables. this result was not entirely surprising since steel mills produce a high amount of ozone and since the CDC has linked ozone to respiratory issues, as mentioned above.


I then decided to gauge whether there was a significant linear relationship between steel mill presence and deaths per positive case. Repeating the same process as above, I obtained the following results:

<p align="center">
  <img src="https://github.com/bcerminarache2410/CHE2410-Project-1/blob/main/mill%20presence%20vs%20death%20rate%20-%20with%20reg.png" width="350"><br>
  <img src="https://github.com/bcerminarache2410/CHE2410-Project-1/blob/main/mill%20presence%20vs%20death%20rate%20-%20reg%20nums.png" width="500">
</p>

In this case the P-value of the slope parameter prevents me from rejecting the null hypthosis that is is equal to zero. Therefore, I cannot confidently conclude that there is a significant relationship where steel mill presence increases deaths per positive case.


Finally, I decided to run an interaction analysis between ozone pollution, steel mill presence, and death rate. To transform my air pollution data into a workable format for this test, I had to get it into the form of a list of ones and zeros. To do so, I referenced the EPA's "safe" limit for ground-level 8-hr ozone concentration average, which is equal to 0.07 PPM. I created a list that defined values of concentration below that level as a zero and those equal to or above that level as one.

I then ran a linear regression analysis for an interactive equation of the following form:
### $Death Rate = const + x_1(mill presence) + x_2(ozone level) + x_3(mill presence)(ozone level)$

Upon running the linear regression model for this test and obtaining the following results, I was unable to confidently say that the three metrics had an interaction that followed a linear fit.

<p align="center">
  <img src="https://github.com/bcerminarache2410/CHE2410-Project-1/blob/main/interaction%20reg%20nums.png" width="500">
</p>

## Conclusion

After performing the above analyses, only one of the linear relationships proided a confident result, and that relationship was already expected. I am thus able to reject my hypothesis that steel mill presence raises the death rate on a county level. I also have to concede that my model could not say with confidence that higher levels of ozone pollution led to increased risk.
