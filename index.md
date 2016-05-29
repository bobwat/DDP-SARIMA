---

title       : ARIMA Seasonality Demonstrator
subtitle    : Developing Data Products Project
author      : Bob Waters
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]     # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

---
 
## Shiny App to Demonstrate Seasonality on ARIMA Models
- ARIMA Autoregressive Integrated Moving Average
- Describe Time Series Data and Forecast Future Values
Seasonal ARIMA Model
$$(p,d,q)\times(P,D,Q)_s$$
- $p$: Autoregressive process order
- $d$: Differencing term
- $q$: Moving average process order

- $P$: Seasonal autoregressive order
- $D$: Seasonal differencing
- $Q$: Seasonal moving average order
- $s$: Seasonality

--- .class #id 
## Mauna Loa Atmospheric CO2 Concentration
- Monthly Data, seasonality = 12
- In base R as co2
- Last 120 entries of the time series

![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png)


--- .class #id 

## auto.arima() Function
- The R forecast package by R.Hyndman
- Specify the seasonality
- auto.arima varies the orders of the function, and calculates models
- Model with the lowest AIC is chosen as the best of the models calculated

```
## Series: x 
## ARIMA(1,0,1)(0,1,2)[12] with drift         
## 
## Coefficients:
##          ar1      ma1     sma1     sma2   drift
##       0.8952  -0.2425  -0.6085  -0.1856  0.1097
## s.e.  0.0581   0.1301   0.1052   0.1120  0.0066
## 
## sigma^2 estimated as 0.09633:  log likelihood=-27.13
## AIC=92.01   AICc=92.83   BIC=108.16
```

--- .class #id
## Residual Autocorrelation and Partial Autocorrelation
- Used to determine the resulting noise is independent and identically distributed
- The noise within the 95% CI is most likely to be iid

![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-1.png)
- User can adjust seasonality and determine (or demonstrate) the seasonality is 12
