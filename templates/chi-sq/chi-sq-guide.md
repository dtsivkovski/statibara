---
layout: base
search_exclude: true
permalink: /x2/guide/
categories: Chi-Squared Tests
---

{% include capybar.html %}

# A Guide to Chi-Squared Tests for Inference

## Differences Between the Tests

| Category | Goodness of Fit | Test for Independence | Test for Homogeneity |
|:---------------:|:---------------:|:---------------------:|:--------------------:|
| **Number of Categorical Variables** | 1 | 2 | 2 |
| **Number of Samples** | 1 | 1 | 2+ |
| **Data for Input** | Observed + Expected | Observed Only | Observed Only |
| **Null Hypothesis** | **Ho:** Observed = Expected | **Ho:** Variables are independent | **Ho:** There is no difference in the distributions |
| **Alternative Hypothesis** | **Ha:** Observed != Expected | **Ha:** Variables are not independent | **Ha:** There is a difference in the distributions |


## State

In the state step, you must include the null hypothesis, alternative hypothesis, and the alpha value. The alpha value is just like in the other tests, usually ranging from 0.01 to 0.10 (for reasonable alpha values). The hypotheses, however, are different depending on which chi-squared test you are performing, so you should refer to the table above.

## Plan

In the plan step, you must first state the name of the test you are performing. Then, you must check all of the conditions necessary for the test in order to proceed to the next steps.

- Random: The data must be collected randomly, whether through a random sample or random assignment. 
    - Note: If it is random assignment, the test immediately becomes a chi-squared test for homogeneity because that is considered as two samples.
- Independence (10%): Each sample/group must be less than 10% of the entire population that it is being taken from. This is to ensure that the samples are independent of each other.
- Normal: Each expected value must be at least 5. 
    - Goodness of Fit: The expected values are calculated by multiplying the total number of observations by the proportion of each category in the population. 
    - Independence/Homogeneity: The expected values are calculated by multiplying the row total by the column total, and dividing by the total number of observations.

