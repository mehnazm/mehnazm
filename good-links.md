---
layout: page
title: Good Links
permalink: /good-links/
---


Here is a list of links to insights that I found really interesting. I will continue to add more, both old and new (will limit it to under 100 links to prioritize what was most meaningful)

## 1. Metrics

### 1.1. General

1.1.1. [Don't Let Your North Star Metric Deceive You](https://brianbalfour.com/essays/north-star-metric-growth) - A great critique of the limitations of OMTM. Specifically it points out that North Star metrics are 1)Output metrics: too big, broad, not actionable. It's like a scoreboard for a game. (My wording: it just states the obvious in numerical terms, without any insight on what needs to be done) 2)Output metrics are lagging indicators. For instance, if we only pay attention to revenue and not product usage frequency by paying customers, we will only become aware of product problems when users churn at the end of their subscription period. 3)It only captures one dimension of the business,leading to over-optimization at the expense of other dimensions. It doesn't account for trade-offs, reminiscent of the Instrumental Convergence/Paperclip Fallacy. For example, monetization may be pursued at the expense of retention, or exploitation (producing yet another movie sequel) at the expense of exploration (creating something novel and refreshing). One critique I have of this blog post is that while I appreciate it drawing a distinction between input and output metrics, some of the input metrics are only inputs with respect to the final output metric-they are not inputs i.e. actionable from the business perspective. Metrics such as "Bring users back more often" are intermediate metrics between actual business levers or inputs and desired final output.

1.1.2. [Don’t Become a Victim of One Key Metric](https://caseyaccidental.com/one-key-metric-victim) -  An example here reminded me of the Munger quote, 'Show me the incentive and I'll show you the outcome.' Grubhub and Seamless had similar businesses with very different key metrics. Grubhub optimized for revenue, while Seamless optimized for GMV. Consequently, Seamless would show restaurants in alphabetical order in their search results, while Grubhub sorted restaurants by the average commission they earned from orders. Another example discussed how Pinterest's metric ended up incentivizing the algorithm to show clickbait images, with the comment, 'The metrics make it appear that engagement is increasing. It might be, but it is an empty calorie form that will affect engagement in a very negative way over the long term.' This made me reflect on how I try to stay away from Instagram after consuming enough 'empty calories' there, leading to a step function change in my usage after a period of high activity.

1.1.3. [Common Mistakes In Defining Metrics](https://brianbalfour.com/quick-takes/common-mistakes-defining-metrics) - This is where I first read about and realized engagement is depth and retention is binary. I keep thinking of this article ever so often and so this definitely needed a spot in this list, since I know I will be looking for it in future.

1.1.4. [Bezos on managing to metrics](https://www.youtube.com/watch?v=8ij964FCQiw) - Keeping this here as a note to remember Goodhart's Law-even though it is a familiar concept, it's easy to fall for it unless vigilant.

1.1.5. [What Moneyball-for-Everything Has Done to American Culture](https://www.theatlantic.com/newsletters/archive/2022/10/sabermetrics-analytics-ruined-baseball-sports-music-film/671924/) - Argues that the analytics revoultion has approached sports,music and movies like an equation and "solved" it-in the process making them more homogenous. It sacrifices exuberance for the sake of formulaic symmetry. It sacrifices diversity for the sake of familiarity. This is interesting-while I have definitely observed what the article argues, at the same time we can also observe how the internet has created many subcultures and niche interests. I am not sure how to tie these contradictory observations, but it is something worth chewing on.


### 1.2. Growth Metrics

1.2.1. [Your Average CAC is Lying to You -- What to do Instead](https://brianbalfour.com/essays/average-cac-mistakes-growth) - Talks about the importance of looking at segmented CAC vs LTV instead of average CAC vs LTV. Segmentation may be based on Customer Type (e.g. Tier), Channel (e.g. FB, Twitter, Google), Geography etc. Additionally CAC changes over time-channel based evolution or network-effect evolution may reduce CAC over time whereas saturation-based evolution increases CAC.

1.2.3. [How To (Actually) Calculate CAC](https://andrewchen.com/how-to-actually-calculate-cac/) - Makes a distinction between CAC (acquiring customers) and CPA (acquiring leading indicators to paying customers). Makes the point that CAC should be based on length of sales cycle, distinguish between new vs. returning customers and be fully loaded i.e. account for all the sales and marketing salaries, overhead costs. My question here though is how often might length of sales cycle change? How often do we check for it? What would be the implication of longer CAC maturity?

### 1.3. Product Metrics

1.3.1. [A Deep Dive Into User Engagement Through Tricky Averages](https://dataanalysis.substack.com/p/a-deep-dive-into-user-engagement) - I appreciate this article for putting into writing and serving as a reminder for a common problem anyone working with data has experienced/will continue to experience. Essentially, the denominator that is chosen to calculate per user averages can change the story being told. The story changes because the user segments (and therefore user behavior) captured changes with the choice of denominator. It is a reminder to have more clarity and specificity on what we want to know. The right method of average per user metric depends on the question being asked.

1.3.2. [Retention Benchmarks](https://brianbalfour.com/quick-takes/retention-benchmarks) - I am very wary of averages and blended metrics, and even so this article gave me yet another point against averages- Averages are useless.  You want to benchmark against best in class. Another interesting learning from this was the point around when low retention is ok-anything with low acquisition and marginal costs but power law returns. Additionally, I also liked the Gusto example on knowing what you can and cannot influence i.e. since Gusto cannot influence how many employees thier customers hire, they can only maintain their customers and no expand. What they can go after is greater wallet share but offering more product lines.

### 1.4. Financial Metrics


## 2. Formulas and Models

## 3. A/B Testing

3.1. [5 warning signs: Does A/B testing lead to crappy products?](https://andrewchen.com/does-ab-testing-lead-to-crappy-products/) - Keeping this article as a source of reference that clearly articulates common concerns around AB testing. The point on "Quitting too early" is one that has always concerned me. It especially applies when page redesigns are done and returning customers react badly to it. Questions arise: Do we wait for returning users to adjust to the changes or do we revert to how things were? What is sufficient time to allow behavior change? Is it worth accepting negative impact on revenue metrics while we hope for users to hit a steady state in their response? These are perhaps philosophical questions, in the same category as When is the right time to pivot a business? When is it the right time to give up on something? But these often creep into the scope of AB tests. 

3.2. [Are RCTs a good way to do economics](https://someunpleasant.substack.com/p/real-chaos-today?utm_source=post-email-title&publication_id=261003&post_id=59956889&utm_campaign=email-post-title&isFreemail=true&r=9hzj0&triedRedirect=true&utm_medium=email) - I found this interesting because the concerns it articulates around RCTs parallel the ones I have with A/B testing. For instance, that not everything is tractable to RCTs; there are concerns about external validity and whether RCTs produce generalizable knowledge; the bias-variance tradeoff for internal validity; and whether the average effect is the most relevant statistic (in contrast to measures of questions such as “who benefits the most”, “how much do group X and group Y benefit”, “over what timeframe are benefits fully accrued”) -these are all concerns that are very relevant to AB testing. Also, I found the concluding line "Ultimately, why projects work is, fundamentally, a better question than whether they work." quite thought-provoking. 


## 4. Growth

## 5. Product

### 5.1 Onboarding

## 6. Marketplace

6.1. [Developing a growth model + marketplace growth strategy](https://www.youtube.com/watch?v=AlTQ6O2qooI) - Some takeaways from this: 1)Retention is likely the most important growth metric 2)Retention is the hardest to move but core product levers such as depth of supply, interaction with supply matters more than growth levers like notificaitons 3)Early lifecycle experience is a good indicator of future retention (and so early intervention is more effective than when customers are about to churn). On a separate note, a common analytical failure mode: "Our best users do x, why can't we make others do the same". This generally does not work-the others have different intent/context. The goal would be to figure out where the value for "the others" lie. Regarding marketplace expansion, might make more sense to after adjacent/easier/network effect accentuating space compared to higher TAM. Also, product i.e. incredible E2E experience (atomic networks?) matters more than GTM investments in liquidity (@45:30). 

## 7. ECommerce

## 8. Statistics

## 9. Big Picture

9.1. [Disrupting Disruption](https://every.to/divinations/disrupting-disruption-734208) - A thought provoking challenge to Clayton Christensen's Disruption Theory. I liked the use of concrete examples such as Uber, iPhone, Costco, Walmart, Southwest Airlines.

9.2. [Complexity Convection](https://every.to/divinations/complexity-convection-765851) - This article stayed with me for its insights on the value of keeping products and businesses simple and the pressures and incentives that work against it.

9.3. [Publishers and the Smiling Curve](https://stratechery.com/2014/publishers-smiling-curve/) - This is where I first learned about the Smiling Curve. Ben Thompson's application of the framework to the publishing industry is an eye-opener, as it makes you consider the commonalities between seemingly disconnected industries.

9.4. [What Strategy Questions are You Asking](https://rogermartin.medium.com/what-strategy-questions-are-you-asking-587d32239a48) - I appreciated this article for highlighting that "moat" is dynamic and ever-changing. The true advantage lies in being ahead enough to ask and answer questions that competitors are not yet in a position to think about. It also asserts that a data advantage is really a questions advantage and that data analysis without a hypothesis is just data mining. This really resonated with me because speaking from experience, it's easy to fool ourselves and others with numbers and charts, mistaking complexity or effort for meaning. But that is ultimately noise. The framing—the questions—is the most important thing.













 










