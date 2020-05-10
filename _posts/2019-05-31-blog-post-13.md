---
title: "Standard Errors in Regression"
date: 2019-12-31
permalink: /posts/2019/12/blog-post-13/standard-errors
redirect_from: /posts/2019/12/blog-post-13/
tags:
  - Error
  - Regression
---

<b>Errors in the Regression Equation:</b>
There is always some error associated with the measurement of any signal. Earlier, we saw how this affected replicate measurements, and could be treated statistically in terms of the mean and standard deviation.

The same phenomenon applies to each measurement taken in the course of constructing a calibration curve, causing a variation in the slope and intercept of the calculated regression line. This can be reduced - though never completely eliminated - by making replicate measurements for each standard.
Even with this precaution, we still need some way of estimating the likely error (or uncertainty) in the slope and intercept, and the corresponding uncertainty associated with any concentrations determined using the regression line as a calibration function.<br>
<br>
<b>The Uncertainty of the Regression:</b>
We saw earlier that the spread of the actual calibration points either side of the line of regression of y on x (which we are using as our calibration function) can be expressed in terms of the regression residuals, (yi − ): The greater these resdiuals, the greater the uncertainty in where the true regression line actually lies. The uncertainty in the regression is therefore calculated in terms of these residuals. Technically, this is the standard error of the regression, sy/x:

```
SE = sqrt(sum(y[i]-yhat[i])/n-2)
```

Note that there are (n − 2) degrees of freedom in calculating sy/x. This is because we are making two assumptions in this equation: a) that the sample population is representative of the entire population, and b) that the  values are representative of the true y-values. For each assumption, we remove one degree of freedom, and our estimated standard deviation becomes larger.
<br>
Another way of understanding the degrees of freedom is to note that we are estimating two parameters from the regression – the slope and the intercept. Therefore, ν = n − 2 and we need at least three points to perform the regression analysis.
<br>
<br>

<b>The Uncertainty of the Slope:</b>
The slope of the regression line is obviously important, as it determines the sensitivity of the calibration function; that is, the rate at which the signal changes with concentration. The higher (steeper) the slope, the easier it is to distinguish between concentrations which are close to one another. (Technically, the greater the resolution in concentration terms.) The uncertainty in the slope is expressed as the standard error (or deviation) of the slope, sb, and is calculated in terms of the standard error of the regression as:

```
S_b = SE/sqrt(sum(x[i]-xmean))
```

The corresponding confidence interval for the slope is calculated using the t-statistic for (n − 2) degress of freedom as:

```
b ± tn−2sb
```

Remember: here n is the number of calibration points used in the regression calculation.
<br>
<br>
<b>The Uncertainty of the Intercept:</b>
The intercept of the regression line has implications for both the smallest detectable signal (measured response) and the corresponding lowest detectable concentration. The uncertainty in the intercept is also calculated in terms of the standard error of the regression as the standard error (or deviation) of the intercept, sa:

```
S_intercept = SE.sqrt(sum(x[i]**2)/n.sum((x[i]-mean)**2))
```

The corresponding confidence interval for the intercept is calculated in the same way as that for the slope, namely:
```
a ± tn−2sa
```