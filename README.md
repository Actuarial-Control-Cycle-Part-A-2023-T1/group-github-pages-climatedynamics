[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-8d59dc4de5201274e310e4c54b9627a8934c3b88527886e3b421487c677d23eb.svg)](https://classroom.github.com/a/elzutNYu)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-f4981d0f882b2a3f0472912d15f9806d57e124e0fc890972558857b51b24a6f9.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=10712948)
# Actuarial Theory and Practice A @ UNSW

_"Tell me and I forget. Teach me and I remember. Involve me and I learn" - Benjamin Franklin_

---

### Congrats on completing the [2023 SOA Research Challenge](https://www.soa.org/research/opportunities/2023-student-research-case-study-challenge/)!

Our group is ClimateDynamics

> Now it's time to build your own website to showcase your work.  
>To create a website on GitHub Pages to showcase your work is very easy.

This is written in markdown language. 
>
* Click [link](https://classroom.github.com/a/elzutNYu) to accept your group assignment.


#### Follow the [guide doc](Doc1.pdf) to submit your work. 
---
>Be creative! Feel free to link to embed your [data](hazard-event-data.csv), [code](sample-data-clean.ipynb), [image](unsw.png) here

More information on GitHub Pages can be found [here](https://pages.github.com/)
![](Actuarial.gif)

# Executive summary

# Program design


# Macro-economic, hazard and damage modelling

## Macro-economic variables modelling: 

To take account into the effects of inflation and interest rates on property value and damage data, we build a time-series model to project the future inflation. For model selection, we split the historical inflation rates and interest rates into a training period (before Year 2010) and the validation period (after Year 2010). The model with the lowest validation Mean-Square-Error, which is ARIMA(1,1,0), is chosen as our best estimate for future inflaiton rates and interest rates. The other two models, namely AR(1) and the smoothing spline, are used to form our upper scenario (i.e., high inflation rate) and the lower scenario (i.e., low inflation rate), respecitvely. 

The projections of future inflation rates and interest rates are shown in the following two figures:  

![image](Inflation_rates_projections.png)

![image](Interest_rates_projections.png)



# Pricing and cost

# Risk and Risk mitigation

# Conclusion

