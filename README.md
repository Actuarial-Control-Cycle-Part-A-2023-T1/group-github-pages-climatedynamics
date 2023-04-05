[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-8d59dc4de5201274e310e4c54b9627a8934c3b88527886e3b421487c677d23eb.svg)](https://classroom.github.com/a/elzutNYu)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-f4981d0f882b2a3f0472912d15f9806d57e124e0fc890972558857b51b24a6f9.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=10712948) 

# 2023 SOA Case Study Challenge - A Relocation Social Insurance Program

_"Tell me and I forget. Teach me and I remember. Involve me and I learn" - Benjamin Franklin_ 

### Congrats on completing the [2023 SOA Research Challenge](https://www.soa.org/research/opportunities/2023-student-research-case-study-challenge/)!


> Now it's time to build your own website to showcase your work.  
>To create a website on GitHub Pages to showcase your work is very easy.

This is written in markdown language. 
>
* Click [link](https://classroom.github.com/a/elzutNYu) to accept your group assignment.


#### Follow the [guide doc](Doc1.pdf) to submit your work.  

>Be creative! Feel free to link to embed your [data](hazard-event-data.csv), [code](sample-data-clean.ipynb), [image](unsw.png) here

More information on GitHub Pages can be found [here](https://pages.github.com/)
![](Actuarial.gif) 




Our group is ClimateDynamics

# Executive summary

# Program design


# Macro-economic, hazard and damage modelling

## Macro-economic variables modelling: 

To take account into the effects of inflation and interest rates on property value and damage data, we build a time-series model to project the future inflation. For model selection, we split the historical inflation rates and interest rates into a training period (before Year 2010) and the validation period (after Year 2010). The model with the lowest validation Mean-Square-Error, which is ARIMA(1,1,0), is chosen as our best estimate for future inflaiton rates and interest rates. The other two models, namely AR(1) and the smoothing spline, are used to form our upper scenario (i.e., high inflation rate) and the lower scenario (i.e., low inflation rate), respecitvely. 

The projections of future inflation rates and interest rates are shown in the following two figures:  

Projection of inflation rates          |  Projection of interest rates
:-------------------------:|:-------------------------:
![image](Inflation_rates_projections.png)  |  ![image](InterestRate_projections.png)

## Hazard and damage modelling:

Frequency and severity of hazard loss have been modelled separately in our analysis. We have taken a standard approach and used Poisson regression to model hazard frequency since the count of hazard events is a discrete random variable. In particular we chose a Poisson GAM as it outper-
formed the Poisson GLM with regards to AIC and BIC metrics.

For severity model we chose to model the damage ratio (the ratio of property damage to exposure) instead of the absolute value of property damage, as dollar value of property damage could be heavily influenced by the market value of the property rather than the inherent severity of the
peril. To model the damage we fit a zero adjusted Beta distribution as the damage ratio varies between 0 and 1 and the distribution is highly non-symmetric. 

The fitted frequency and damage models specified above are used to generate projections for future hazard events count and damage ratio. As per the figure below, Region 3 has the highest projected events count. To factor both frequency and severity into risk evaluation, we have developed a climate risk index, defined as the product of predicted events count and the damage ratio. Based on the climate risk index, Region 5 has the highest risk in all projected years.

Projected hazard events count          |  Projected climate risk index
:-------------------------:|:-------------------------:
![image](Projected_Hazard_Events_count.png)  |  ![image](Projected_Hazard_risk_index.png)



# Pricing and cost

# Risk and Risk mitigation

# Conclusion

