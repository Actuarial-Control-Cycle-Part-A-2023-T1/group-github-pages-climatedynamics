
# 2023 SOA Case Study Challenge - A Relocation Social Insurance Program

<!--- [![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-8d59dc4de5201274e310e4c54b9627a8934c3b88527886e3b421487c677d23eb.svg)](https://classroom.github.com/a/elzutNYu)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-f4981d0f882b2a3f0472912d15f9806d57e124e0fc890972558857b51b24a6f9.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=10712948) -->


<!--- _"Tell me and I forget. Teach me and I remember. Involve me and I learn" - Benjamin Franklin_

---

### Congrats on completing the [2023 SOA Research Challenge](https://www.soa.org/research/opportunities/2023-student-research-case-study-challenge/)!

>Now it's time to build your own website to showcase your work.  
>To create a website on GitHub Pages to showcase your work is very easy.

This is written in markdown language. 
>
* Click [link](https://classroom.github.com/a/elzutNYu) to accept your group assignment.


#### Follow the [guide doc](Doc1.pdf) to submit your work. 
---
>Be creative! Feel free to link to embed your [data](hazard-event-data.csv), [code](sample-data-clean.ipynb), [image](unsw.png) here

More information on GitHub Pages can be found [here](https://pages.github.com/)
![](Actuarial.gif) -->



<p float="left">
  <img src="flood.gif"  >
  <img src="insurance2.gif" > 
</p>

---

## Executive summary
We aim to develop a social insurance program which can provide nationwide coverage against displacement due to natural perils in anticipation to the increasing frequency and severity of catastrophic climate events.

The product is designed to be accessible to all, tailored to meet the diverse geographical risks presented by Storslysia's six regions. In our design we focus on accurately forecasting future events so that Storslysia's residents may be relocated promptly, minimising potential costs associated with accommodation, lost of personal effects and psychological pressure. Based on our results, we have found that the relocation program could substantially reduce the economic cost of property damages over the long-term horizon. Additionally, we are 90.69% confident that the program cost will not exceed 10% of the national GDP in any given year by weighting different climate and macro-economic scenarios. 




## Program design

### Claim requirement & coverage

For citizens of Storslysia to submit a valid claim they must meet the following requirements: 
- The claim must be lodged within 6 months of the event which caused the loss.
- Policyholders cannot claim for a natural event which occurs within 72 hours of policy inception.
- The damage must not be a direct result of negligence to maintain the property or improper installation of pipes/circuitry/heaters etc.
- Any information disclosed must be full and truthful. This includes information about the extent of the damage, prior claims history and any other relevant facts[^1]. 

[^1]: Adjusters may decline the claim on the grounds of insufficient or false information.



The social insurance program will cover 50% of the cost for new property, and the rest will come from the owner or private insurance, as well as support for temporary housing. This ensures basic living for households, and low-income households can receive up to 1.5x the coverage. Below is a list of claim coverage, note that the amount is per household unless specified otherwise.

| Coverage Item | Coverage Amount |  Other Conditions |
| :--- | :--- | :---|
| New Housing | 50% (up to 150k) | Limits by region, based on mean price |
| Temporary Housing| up to 1,000/month | This is per person |
| Living Support| up to 3,000 | For low-income households[^2]|
| Moving Cost| up to 6,000 | For low-income households |

[^2]:Defined as households earning less than 50% of median income. 


### Voluntary relocation

Cost reduction benefits resulting from planned relocation can be categorised into two types:

- Relocation priorities and options: Geographical incentives are provided to affected parties to encourage  voluntary relocation, as a wider range of relocation alternatives and faster processing time are offered. This in turn lowers the urgency and need for transport and emergency aid, thus reducing unnecessary costs associated with involuntary relocation. 
- Cost Reduction and Additional Benefits: Households opting for voluntary relocation will have 80% coverage and limits for new housing, be provided with financial support in the form of free moving costs (of Ꝕ4,000) and additional relocation expenses coverage (of Ꝕ2,000) as well as supplementary support such as property/goods relocation services.

Through provision of these benefits we hope to incentivise a greater proportion of individuals at risk to act early to not only reduce costs but also to maintain public safety.  


### Program timeframes
The model monitoring process will involve monthly reporting focusing on relocation costs and actions whereby every month there will be assessment of program progress and market conditions. Voluntary relocation options may be reduced if there is a labour shortage. Model performance will be reviewed annually and the parameters will be calibrated in line with the current years’ economic and climate data. In the case that actual experience deviates greatly from forecasts we may rebuild the economic and hazard models entirely to better predict aggregate cost. The past program costs and coverage will need to be analysed, inflation and GDP increase will also need to be reflected in coverage amounts and excess limits.

In the long run, every ten years the model will undergo a major overhaul. As climate events be- come increasingly unpredictable globally, new findings will be used to rebuild the technical cost model. Emerging technologies will also help to improve costs and efficiency. Detailed list is as below:

| Timeframe | Actions |  Other Changes |
| :--- | :--- | :---|
| 1 Month | Monitor property and construction market <br> Monitor current year's program costs <br> Adjust relocation schedules | National Economic Figures<br>Property/Industry Reports |
| 1 Year | Annual assessment of program costs/coverage <br> Update Hazard Model <br> Update Economic Model <br> Update program coverage limits/amount | National Economic Figures <br> Legal and Policy Change <br> World Economic Outlook <br> Climate Change Report |
| 10 Years | Review program coverage/past results <br> Update/Rebuild Economic Model <br> Update/Rebuild Hazard Model | Major Climate Events <br> Tech Improvement |





## Macro-economic, hazard and damage modelling

### Macro-economic variables modelling: 

To take account into the effects of inflation and interest rates on property value and damage data, we build a time-series model to project the future inflation. For model selection, we split the historical inflation rates and interest rates into a training period (before Year 2010) and the validation period (after Year 2010). The model with the lowest validation Mean-Square-Error, which is ARIMA(1,1,0), is chosen as our best estimate for future inflaiton rates and interest rates. The other two models, namely AR(1) and the smoothing spline, are used to form our upper scenario (i.e., high inflation rate) and the lower scenario (i.e., low inflation rate), respecitvely. 

The projections of future inflation rates and interest rates are shown in the following two figures:  

Projection of inflation rates          |  Projection of interest rates
:-------------------------:|:-------------------------:
![image](Inflation_rates_projections.png)  |  ![image](InterestRate_projections.png)

### Hazard and damage modelling:

Frequency and severity of hazard loss have been modelled separately in our analysis. We have taken a standard approach and used Poisson regression to model hazard frequency since the count of hazard events is a discrete random variable. In particular we chose a Poisson GAM as it outper-
formed the Poisson GLM with regards to AIC and BIC metrics.

For severity model we chose to model the damage ratio (the ratio of property damage to exposure) instead of the absolute value of property damage, as dollar value of property damage could be heavily influenced by the market value of the property rather than the inherent severity of the
peril. To model the damage we fit a zero adjusted Beta distribution as the damage ratio varies between 0 and 1 and the distribution is highly non-symmetric. 

The fitted frequency and damage models specified above are used to generate projections for future hazard events count and damage ratio. As per the figure below, Region 3 has the highest projected events count. To factor both frequency and severity into risk evaluation, we have developed a climate risk index, defined as the product of predicted events count and the damage ratio. Based on the climate risk index, Region 5 has the highest risk in all projected years.

Projected hazard events count          |  Projected climate risk index
:-------------------------:|:-------------------------:
![image](Projected_Hazard_Events_count.png)  |  ![image](Projected_Hazard_risk_index.png)



## Pricing and cost

Based on the results above, Region 5 is deemed to have the highest risk, while Region 1 has the lowest risk. As a result, our program aims to relocate residents from Region 5 to Region 1.

To calculate the potential economic impact of the relocation program, we assume that all residents from Region 5 are successfully relocated to Region 1. The increase in the exposure in Region 1 will be the cost of constructing new houses to accommodate immigrants from Region 5, which could be approximated as: $\tilde{E}_5=H_5\cdot\bar{V}_1$, where $H_i$ is the number of households in region $i$ and $\bar{V}_i$ as the mean housing value in region $i$. We further assume the climate risk in Region 1 stays the same after relocation (i.e., the expected frequency $\hat{N}_1$ and the expected damage ratio $\hat{d}_1$ stay the same), then the new total property damage in Region 1 after relocation will be: $\tilde{D}_1 = (E_1+\tilde{E}_5)\times \hat{d}_1 \times \hat{N}_1$. And the new total property damage in Region 5 will be zero (i.e., $\tilde{D}_5=0$) as we assume all the residents in Region 5 will move to Region 1.

The projected property damage with and without relocation are shown in Figure 1, under the baseline inflation scenario. The difference between the projected property damage becomes more significant in later projected years, which might be explained by the quadratic growth of hazards frequency and the accumulation effects of inflation rates.   

<p align="center">
  <img src="Projected_cost_BeforeandAfterRelocation.png" >
  <br> 
  <em>Figure 1: Property damage before/after relocation.</em>
</p>

Additionally, we have also calculated the present value of expected cost saving from the reduction in projected property damage after the relocation during the next **10-year horizon**. The present value of the total expected cost saving is **Ꝕ6,566,773,052.43**.


### Relocation Costs


The table below lists the costs associated with relocation for the year 2020, using the values for Region 1 as an example. Please note that these figures will be updated annually based on inflation and the respective rates for the upcoming year. Additionally, the potential cost savings from voluntary relocation are more than 3 times the median household income.

| Related Items | Cost(Ꝕ) |  Estimation Method | Avoidable? |
| :--- | :--- | :---| :---|
| New Property Cost | 371,828 | Property value distribution | No |
| -Additional Construction | 111,939 | 50% of construction costs[^3] | Yes |
| Replacing Household Goods | 124,272 | 60% of housing costs | Yes |
| Temporary Housing | 44,064 | | Yes |
| Moving Costs | 4,000 | Industrial averages for USA states | No |
| -Additional Moving Costs | 2,000 | 50% of normal costs | Yes |
| **Avoidable Total** | **282,275** | |

[^3]: Cost estimated using industrial averages for USA states [link](https://www.forbes.com/home-improvement/contractor/cost-to-build-a-house/)


## Risk and Risk mitigation

There are two primary categories of risks: quantifiable risks and qualitative risks. The table below presents examples of each type.


| Qualitative Risks | Quantifiable Risks | 
| :--- | :-------------------------------- | 
| **Availability of new properties:** The availability of new properties can be affected by many factors including limited labour, resources, build permits issued (Region 3 permits issued is only 0.32% of properties), which will be a great issue in events of major hazard events. Voluntary relocation is a big part of mitigation, distributing relocation evenly in advance to ease the peak demand, and government can initiate development projects to build relocation properties in mass. | **Catastrophic Hazard Events:** Large flooding and earthquakes can cause thousands of households to force to relocate. Such events are very hard to forecast but becoming more common with climate change. We have modelled the worst scenario and tested the sustainability of program under stress, and there is a very large increase in severity of damage. |
| **Disruption of Work:** Hazard events can cause damage to commercial properties and affect business activities as well, causing people to lose their job temporarily or permanently. In the program plan there will be loss of income help to households with income below a threshold, to help households in poverty or lost income for the duration of relocation. | **Macro-economic variables:** The inflation rate and interest rates could deviate from the baseline assumptions due to policy changes or external shock to the system. To assess the risk from changing macro-economic environment, we have projected the program cost under the high-inflation scenario, the baseline inflation scenario, and a low inflation scenario. | 



## Conclusion

