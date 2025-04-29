# Sources

For this analysis, the dataset is from Ads Smart. The data has a good overview of basic AB test data related to the conversion rate of users. (https://www.kaggle.com/datasets/osuolaleemmanuel/ad-ab-testing)

# **Project Goals and Tasks**

This AB test provides understanding of whether a product change can result in better interaction from the users, in this case, the conversion rate. With the data available related to the device of the user, we can breakdown whether a specific customer group is performing better with the applied changes. 

The objectives of this analysis include: 

- A Statistical Significance Testing of the AB test to provide an overview of the performance of the test
- Evaluating the results of the AB tests

Why are these objectives important? 

- An AB test observes potential changes without actually implementing them for all customers.
- Understanding the data of AB tests can be conclusive, or not; therefore, not all AB tests can provide all the necessary answers on whether the changes will be successful.
- AB test needs to be concluded in a specific timeframe to provide enough data for conclusive results. During that period, there should be no interlapping AB tests evaluating different changes leading to the same result (eg, multiple changes related to conversion rates).
- Observing the results with different methods can allow us to be certain whether the data is
    - Enough to be conclusive for the results
    - Provide us with an answer on whether the changes are effective or not.
 
### Description of variables
```

auction_id: the unique id of the online user who has been presented the BIO. In standard terminologies this is called an impression id.The user may see the BIO questionnaire but choose not to respond. In that case both the yes and no columns are zero. experiment: which group the user belongs to - control or exposed.
control: users who have been shown a dummy ad
exposed: users who have been shown a creative, an online interactive ad, with the SmartAd brand.
date: the date in YYYY-MM-DD format
hour: the hour of the day in HH format.
device_make: the name of the type of device the user has e.g. Samsung
platform_os: the id of the OS the user has.
browser: the name of the browser the user uses to see the BIO questionnaire.
yes: 1 if the user chooses the “Yes” radio button for the BIO questionnaire.
no: 1 if the user chooses the “No” radio button for the BIO questionnaire.

```

# **Description of Approach**

### **Statistical Significance Testing**

**T-Tests for Response and Conversion Rates**

With T-test we can determine whether the observed differences are statistically significant.

**Bootstrap Analysis for Confidence Intervals**

It helps understand the effect size ranges. The confidence intervals for the difference between groups allows more nuanced information about the effect. 

**Bayesian A/B Testing**

Provides an´overview of whether the controlled group has better responses than the other. 

### **Segmentation Analysis**

- Response Rates by Device
- **Response Rates by Browser and Platform**
- **Response Analysis for Exposed and Control Groups**
- **Response Patterns Over Time**

All those specific analyses can identify patterns of which group of users is performing better. The results can be used for more concrete marketing efforts towards specific customer groups. 

# **Results**
![my_plot.png](https://github.com/cvii-d/ab_test-ads_smart/blob/main/conversion_rate_by_experiment_group.png)

## **Statistical Significance Testing**

**T-Tests for Response and Conversion Rates**

Our p-value below 0.05 typically indicates statistical significance.

```jsx
Response Rate t-test: t-statistic: -2.4985134833114286, p-value: 0.012491258853514858
Conversion Rate t-test: t-statistic: -2.108610239127817, p-value: 0.035008955674483075
```

**Bootstrap Analysis for Confidence Intervals**

Confidence interval 

```jsx
Bootstrap confidence interval for difference in response rates:
95% CI: [0.0045, 0.0359]
```

**Bayesian A/B Testing**

Bayesian A/B test: Probability that exposed is better than control: 0.7398
![my_plot.png](https://github.com/cvii-d/ab_test-ads_smart/blob/main/posterior_distributions_of_conversion_rates.png)

### **Segmentation Analysis**

**Response Analysis for Exposed and Control Groups**

From this overview, the data available is almost equal for both parties, and they all have a very balanced number of responses. In our case, both controlled and exposed groups, around 53-55% have not responded as a result of the changes. 
![my_plot.png](https://github.com/cvii-d/ab_test-ads_smart/blob/main/total_responses_percentages_of_responses.png)

**Response Rates by Device**

The observation shows that the controlled group using Vodafone devices, Xiaomi, and LG performed better than the exposed group. 
![my_plot.png](https://github.com/cvii-d/ab_test-ads_smart/blob/main/response_rate_by_device_type.png)

**Response Rates by Browser and Platform**

When it comes to browsers, the majority of responses are from users with Chrome, especially from the controlled group. As for the Platform, the data is inconclusive as we do not have enough information. 
![my_plot.png](https://github.com/cvii-d/ab_test-ads_smart/blob/main/response_rate_by_browser_and_experiment_group.png)

**Response Patterns Over Time**

1. **Overall Performance**: The exposed group outperforms the control for the conversion rates for dates 3-9 July. However, there is a drop in the exposed group’s performance afterward. 
2. **Peak Performance**: The highest conversion for the exposed group is on 4 July, for the control, 10 July. 
3. **Trend Analysis**:
    - There is a drop on 5 July for the controlled group.
    - Stable performance for the exposed group from 46-49%. Only 1 low point around July 10 (38%)
4. **Crossover Point**: The exposed group performs better than the control group around 9-10 July. 
5. **Volatility**: The exposed group was more volatile compared to the controlled group.
![my_plot.png](https://github.com/cvii-d/ab_test-ads_smart/blob/main/daily_conversion_rates.png)
![my_plot.png](https://github.com/cvii-d/ab_test-ads_smart/blob/main/hourly_converion_rates.png)



## **Further recommendations**

1. **Investigate July 10 Drop**: There can be different issues that need to be taken into consideration, such as technical, seasonal, and major events. 
2. **Consider Longer Testing**: With longer testing time, we can create a better understanding of the effects of the changes and their efficiency. 

# **Conclusion**

It is clear to observe from the data that the group with better performers is the controlled one. However, the sudden drop needs to be further investigated to confirm whether there might be a change that we need to consider. 

Certain groups of customers using specific devices (Vodafone, Xiaomi, LG) have a better response rate than others; however, when it comes to browser or platform they use, the data is less conclusive. 

I can recommend extending the research to create a better image of the performance of the changes, especially in relation to the sudden drop on 10 July. 

Other points which can be useful to observe: 

- Add additional features in the observation, such as demographics (eg, geography, age group)
- Check the performance of customers long term - whether they stay longer using the service.
