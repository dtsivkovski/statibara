---
layout: base
permalink: /x2/guide/
categories: Chi-Squared Tests
---

<head>
    <script type="text/javascript" id="MathJax-script" src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
    <script type="text/javascript" id="jstat" src="https://cdn.jsdelivr.net/npm/jstat@latest/dist/jstat.min.js"></script>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>



<center>

<h1> A Guide to Chi-Squared Tests for Inference </h1>

</center>

## Differences Between the Tests

| Category | Goodness of Fit | Test for Independence | Test for Homogeneity |
|:---------------:|:---------------:|:---------------------:|:--------------------:|
| **Number of Categorical Variables** | 1 | 2 | 2 |
| **Number of Samples** | 1 | 1 | 2+ |
| **Data for Input** | Observed + Expected | Observed Only | Observed Only |
| **Null Hypothesis** | **H<sub>0</sub>:** Observed values equal the expected values | **H<sub>0</sub>:** Variables are independent | **H<sub>0</sub>:** There is no difference in the distributions |
| **Alternative Hypothesis** | **H<sub>a</sub>:** Observed values do not equal the expected values | **H<sub>a</sub>:** Variables are not independent | **H<sub>a</sub>:** There is a difference in the distributions |

<hr>

## "State" Step

In the state step, you must include the null hypothesis, alternative hypothesis, and the alpha value. The alpha value is just like in the other tests, usually ranging from 0.01 to 0.10 (for reasonable alpha values). The hypotheses, however, are different depending on which chi-squared test you are performing, so you should refer to the table above.

<br>
<hr>

## "Plan" Step

In the plan step, you must first state the name of the test you are performing. Then, you must check all of the conditions necessary for the test in order to proceed to the next steps.

- Random: The data must be collected randomly, whether through a random sample or random assignment. 
    - Note: If it is random assignment, the test immediately becomes a chi-squared test for homogeneity because that is considered as two samples.
- Independence (10%): Each sample/group must be less than 10% of the entire population that it is being taken from. This is to ensure that the samples are independent of each other.
- Normal: Each expected value must be at least 5. 
    - Goodness of Fit: The expected values are calculated by multiplying the total number of observations by the proportion of each category in the population. 
    - Independence/Homogeneity: The expected values are calculated by multiplying the row total by the column total, and dividing by the total number of observations.

<br>
<hr>

## "Do" Step

In the do step, you calculate the test statistic, degrees of freedom, and the p-value of such a test.

### Degrees of Freedom (df):
- Goodness of Fit: `df = k - 1`, where k is the number of categories
- Independence/Homogeneity: `df = (r - 1)(c - 1)`, where `r` is the number of rows and `c` is the number of columns

### Test Statistic:

To get the test statistic, first subtract the observed value minus the expected value, square it, and then divide by the expected value. Then, add all of these values together for all cells to get the test statistic.

<div id="testStatistic"></div>
<script>
    document.getElementById("testStatistic").style.fontSize = "x-large";
    var formula = "$$\\chi^2 = \\sum \\frac{(O - E)^2}{E}$$";
    document.getElementById("testStatistic").innerHTML = formula;
    // typeset formula to test statistic element
    MathJax.typesetPromise([document.getElementById("testStatistic")], formula).then(function () {}).catch(function (err) {});
</script>

### P-Value:

To get the p-value, use the degrees of freedom and the test statistic in a chi-squared distribution table or a calculator.
- Calculator: Use the chi-squared cdf function, with the test statistic as the first argument and the degrees of freedom as the second argument.
- Table: The table should have the test statistic, degrees of freedom, and the p-value labeled. Use the two which you have to find the missing p-value.

To see an interactive chi-squared distribution graph, you can visit [Stapplet's Chi-Squared Distribution Graph](https://stapplet.com/x2dist.html) that allows you to visualize what the graph looks like with different degrees of freedom.

<!-- Embed Stapplet Page - Not implemented right now
<iframe src="https://stapplet.com/x2dist.html" style="background-color: white; width: 800px; height: 500px">

-->

<br>
<hr>

## "Conclude" Step

To conclude the test, you must compare your p-value to your alpha much like in other tests. Reject the null if the p-value is lower than the alpha, and fail to reject it if the p-value is higher than the alpha. Make sure you state your conclusion in context.

<br>
<hr>

## "Follow-Up" Step

If you reject the null hypothesis, you must state the cell that most significantly contributed to your chi-squared test statistic. With this, you must also state the observed value of this cell and whether it was higher/lower than the expected value. **This is not necessary if you fail to reject the null hypothesis.**
- Example: <i>"The cell for "Most Likely" in the "United States" sample contributed the greatest to the chi-squared statistic because the observed value of 87 was much greater than the expected value of 21." </i>

<br>
<hr>

<center>

<h1> Related Calculators</h1>

Now, you can try your hand at the chi-squared tests on your own and use these calculators to check your work!

<br/><br/>

</center>

<center>
<button class="button" onclick="window.location.href='{{baseurl}}/x2/gof/'" title="Calculator for Chi-Squared Goodness of Fit Test">Goodness of Fit Calculator</button>
<button class="button" onclick="window.location.href='{{baseurl}}/x2/2-way/'" title="Calculator for Chi-Squared Two-Way Tests">Test for Independence Calculator</button>
<button class="button" onclick="window.location.href='{{baseurl}}/x2/2-way/'" title="Calculator for Chi-Squared Two-Way Tests">Test for Homogeneity Calculator</button>
</center>