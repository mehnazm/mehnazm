---
layout: post
title: "My synthesis of A/B testing"
date: 2024-08-15
---

1. **Deciding on the metrics to measure:**

When A/B testing to quantify, this part may be straightforward since quantification is generally of some standard business metric. When A/B testing to make a decision, this step involves selecting both success and tradeoff metrics. It may also involve choosing metrics that increase the chances of the test being conclusive and/or concluding faster. For example, if a new feature impacts GMV per user through conversion rates, the latter may be a better metric to track as it has less variability, thus requiring fewer samples for the test to conclude. Additionally, it is important to ask if the metric to be tested is actually an input metric that can be moved, if the metric corresponds to a rare event that is not measurable by A/B testing and in general the thinking expressed in the Metrics section above.

2. **The amount of change we want to measure:** 

This is determining the threshold of change we need to know for **practical** reasons around planning and decision making. Are we happy with knowing at least 10% change in GMV? Or does it have to be at least 1%? Or do we have to drill down to the accuracy of 0.1% changes in GMV?

3. **Accounting for outliers:**

It is critical to remove outliers from experiment measurements because they not only skew average values but also increase variance, making the experiment inconclusive. Outliers can be managed by capping observations. For example, human users are unlikely to perform a search several hundred times or have more than a thousand pageviews in a day. In such cases, outliers are likely bots that can be eliminated by imposing search and/or pageview thresholds.Similarly, ad revenue may be disproportionately influenced by a few clicks with very high costs per click. Marketplace GMV (Gross Merchandise Value) may be heavily driven by a few large sellers who have very different behaviors and responses compared to the median user we are interested in during a test. In such cases, capping may still be applicable, or we may want to separate these outliers into different segments and analyze their behavior separately. Often, it is tempting to use a “set and forget” outlier threshold, but depending on the importance of the experiment, it might be worth considering what outliers mean in the specific context of the experiment.

4. **The amount of change we can measure with statistical significance given a combination of testing timeline, % of target population addressed and number of metrics to be measured:**

How much movement of a metric we can attribute to the test depends on the natural variability of the metric. The larger the sample size, the more stable i.e. the less variable the metric and therefore the more chances of being able to detect small changes in the metric as a result of the test. The greater the % of target population addressed and with slight exceptions, the longer the testing timeline, the larger the sample size. The more metrics we want to measure, the more chances of running into false positives (the multiple comparisons problem) -something that can be managed by Bonferroni corrections for example. Often there may be business reasons to want to shorten the testing timeline or minimize population to be used for testing, a table illustrating the combination of timeline and population size with their corresponding minimum detectable effect, would give a clearer picture of the tradeoffs between the amount of change we want to measure, how long we want to measure for and many users we want to measure with. 

5. **Are there any risks to the internal validity of the A/B test:**

    5.1. **Test and control are not independent:**
    
    When the test and/or control group can influence each other, it can lead to over or under estimation of impact measurement. These examples from [Lyft](https://eng.lyft.com/experimentation-in-a-ridesharing-marketplace-b39db027a66e) and [eBay](https://dominiccoey.github.io/assets/papers/marketplace_experiments.pdf) demonstrate that naively partitioning users into treatment and control groups violates the independence assumption and bias the effect estimates; using coarser randomization units —such as regions or auctions respectively instead of users in the context of these examples—may help mitigate the bias (however increase variance). 

    5.2. **Test and control are unbalanced:**
    
    Referred to as Sample Ratio Mismatch i.e. the ratio of actual samples in test and control are different from the intended split due to selection bias,  violating the assumption of random assignment. As in the case of [Doordash](https://doordash.engineering/2023/10/17/addressing-the-challenges-of-sample-ratio-mismatch-in-a-b-testing/), the selection bias may occur during variant assignment such as when the small group of power users all end up in treatment or it can occur during the test such as due to exposure to bugs in one of the groups. 

    5.3. **Interactions between experiments either due collisions or carryover:**
    
    When multiple experiments run concurrently, the same user may be part of more than one experiment. While a full factorial experiment design generally mitigates this issue, there are instances where being in two treatments simultaneously can result in a poor user experience. For example, one experiment might test a blue button while another tests a blue background. Such experiment collisions can lead to results that either overestimate or underestimate the true impact. Similarly, users may be affected by residual effects from prior experiments. For instance, if there are two sequential tests for an ads module, users in the test group for the first experiment may exhibit ads fatigue in the second experiment. This decreased responsiveness to ads is due to fatigue, not necessarily because the ads in the second experiment are ineffective. As a result, the second experiment might show lower lift even if the test group from the first experiment is equally distributed across the test and control groups of the second experiment.

6. **Are there any risks to the external validity of the A/B test:**

    This means the test may not generalize across time and populations i.e. segments, regions

    1. **Seasonality:**
    
    The impact of the experiment may change by hour of the day, day of the week, time of the year.  For example, running promotions may show higher incremental lift during the holiday season compared to other times of the year.

    2. **Novelty:**
    
    Users might engage with a change out of curiosity rather than finding it inherently valuable. To check for the novelty effect, we segment users into new vs. returning. [If the feature is winning for returning users but not for new users, it strongly suggests novelty effect dynamics. ](https://productds.com/images/novelty_effect.html)Another way is to plot usage over time—if there is a spike followed by a decline, it is likely due to the novelty effect.

    3. **Pull forward effect:**
    
    Unlike novelty, where curiosity drives engagement, this effect occurs when users respond positively because the offering has value. However, the observed lift may be illusory. For instance, promotions might drive an increase in business metrics, but this could be “borrowed” from future sales. Following test and control groups over a longer period might show a flattening of impact, as those who took advantage of the promotion may exhaust their demand, leading to lower future purchases compared to the control group.

    4. **Change aversion:**
    
    This is the opposite of the novelty effect. New users may be quick to adopt but returning users may have no or low or delayed adoption. The ShopKick example from the Root Cause Analysis section is fitting here.

    5. **Time to react:**
    
    While this may appear similar to change aversion, in this case users just need time to make changes on their end to take advantage of the new offering. For instance, if a [marketplace tests seller incentives to increase monthly listings](https://mehnazm.github.io/main/2024/06/27/main-post.html), the test may need to for months to allow sellers time to ramp up their inventory. Like the pull-forward effect, a standard 1-2 week A/B testing period might not capture the true impact of the change, even if the sample size is sufficient to signal beyond natural variability.

There are many other scenarios where external validity may be compromised. For example, a change in the search algorithm that initially results in poorer outcomes may increase searches in the short term but reduce them in the long term if users switch to a better search engine. More ads might increase short-term revenue but cause user fatigue in the long run. Algorithms designed to be addictive might boost short-term engagement but lead to long-term churn as users seek a “digital detox.”

As the common financial disclaimer states, “Past performance does not guarantee future results.” This principle aligns with the Turkey illusion, which illustrates the danger of assuming that current trends will continue indefinitely without considering broader contexts or potential future changes e.g. in the economy, government policies, competition or even due to cannibalization. External validity heavily depends on context and it's worth thinking through the extent of generalization we want vs. may be able to have through the A/B test.

7. **Anticipating deep dive questions:**

This involves thinking ahead of what we would want to know both for fixing if things go wrong or for the next iteration even if things go right. Realistically, it is not possible to anticipate all deep dive questions-and some may only come from stakeholders with the benefit of a different perspective, only after they have been exposed to the experiment-however some level of preplanning is necessary to set up the data pipeline to answer such questions.

8. **Instrumentation:**

This is the process of defining data events and configuring tools to track and collect those events, especially applicable when testing a new product or feature; but may also be required when measuring new metrics for an existing feature. Instrumentation is elaborated in the Event Tracking section later. 

9. **Ensuring Alignment of Analysis Approach and Randomization Unit:**

As a rule of thumb, the randomization unit can not be more granular than the analysis unit as that breaks internal validity.  For example, as noted in “[Trustworthy Online Controlled Experiments](https://www.cambridge.org/core/books/trustworthy-online-controlled-experiments/D97B26382EB0EB2DC2019A7A7B518F59),” “if an experiment is using page-level randomization, and a user’s first query is in the Treatment and the feature leads to poor search results, the user may issue a reformulated second query that ends up in the Control.” Moreover, broader commentary cannot be made using granular randomization-to quote the book once again: “Similarly, if metrics are computed across that level of granularity, then they cannot be used to measure the results. For example, an experiment that uses page-level randomization cannot measure whether the Treatment impacts the total number of user sessions.”

When the analysis unit is more granular than the randomization unit, we need to verify our calculations for variance and statistical significance (also referred from the same book). For instance, click-through rate (CTR) is defined as the ratio of total clicks to total pageviews, making the analysis unit a pageview or click. If the experiment is randomized at the user level, this can complicate variance estimation. The variance formula assumes independently identically distributed (i.i.d.) samples, an assumption that holds when the analysis unit matches the randomization unit. However, for page-level metrics like CTR with user-level randomization, samples from the same user can be correlated, causing the simple variance formula to be biased. For certain metrics that cannot be expressed as a ratio of user-level metrics, such as the 90th percentile of page load time, alternative methods like bootstrapping may be necessary.

Even when randomization and analysis units are at the same level of granularity, in cases where the metric is calculated at a relative level (e.g., % delta) rather than in absolute terms, modified variance and statistical significance calculations are required.

10. **What is the ramp plan and kill criteria? What happens if our test group has stat sig negative daily values but is not negative on a cumulative level? How do we ensure we are not susceptible to p-hacking (by for eg. peeking):**

Staged ramps balance speed, risk, and quality. Initially a 5% ramp may be done for a couple of days to make sure there are no bugs in the treatment or experimental setup e.g. in event tracking. Next, depending on how risky the experiment is to the business, either a 25% or a 50% ramp is done. In risky experiments, there is more willingness to trade off speed to ensure nothing is broken and no damage is done to customer experience or the business. In this case, we may hold at 25% to ensure there is no significant negativity in the key metrics (note: not necessarily statistically significant negativity, but negative impact that is significant in the context of the experimental budget), after which we may ramp up to the full power of 50%. We hold at 50% for a predetermined time to ensure statistically significant measurement of the metrics.

BUs and PMs often wish to continuously monitor experiments. I believe this is fine insofar as we are monitoring to ensure there is no significant negativity to the business—for which a predetermined ramp-down plan should be in place. However, intermediate results should not be deemed statistically significant, even if daily data shows statistically significant differences. Statistical significance should be based on the predetermined fixed time horizon for the experiment that fully accounts for metric variability. Daily fluctuations may not represent true population behavior due to potential one-off events skewing the data.

While some platforms use sequential tests for [always-valid p-values](http://library.usc.edu.ph/ACM/KKD%202017/pdfs/p1517.pdf) or [Bayesian testing frameworks](https://ieeexplore.ieee.org/document/7796910/) which allow early stops when intermediate data indicates statistical significance, the industry standard remains classic fixed-horizon testing. In the latter approach, claiming statistical significance before the data has fully settled can lead to [false positives via p-hacking](https://statisticsbyjim.com/hypothesis-testing/p-hacking/).
