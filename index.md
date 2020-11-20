## My DS22 Project: How Far Off Were the 2020 Polls? 

---

For the recent 2020 election cycle, we had the day off at Lambda School, and I was glued to watching the votes come in hour by hour whilst comparing my personal predicted map from 538ToWin against the actual election results. My friends and I had a watch party where the 2016 election was heavily predicted for Hillary Clinton to win (insert HuffPo graphic here), and Nate Silver of the infamous news website FiveThirtyEight was being criticized on all fronts for only giving Clinton a 78% chance to win the election. Nate Silver was of national recognition for having applied statistical analysis techniques to the field of sabermetrics, and applying similar methods to political races using recency and poll grading techniques. 

<img src="images/huffpo.png?raw=true"/>

It’s interesting to note that 2016 wasn’t the worst year for mispredicting a candidate’s performance in the polls: Trump and Clinton both outperformed their expected percentages, and Trump’s wins were concentrated in smaller states which allowed him to net a win through the electoral college system while losing the popular vote. We can go back to 1948 where Thomas Dewey was expected to defeat Harry Truman by a large margin, and one newspaper had even famously misprinted the opposite result of ‘Dewey Defeats Truman’. This was due to the election’s result not being finalized at the time of printing, and many copies had circulated before realizing the error. In actuality, at a national level the 2016 polls were off by a value of 6.27%, where the last error of this magnitude had occurred in 1992. Democrats severely underperformed their polls, and Republicans only slightly overperformed their polls. 

<img src="images/dewey_defeats_truman.png?raw=true"/>

Hoping to see a historic trend of Democrats underperforming and Republicans overperforming, I eventually found that there’s only a very weak correlation (r^2=0.577) between Republicans beating the polls, and no evidence for Democrats (r^2 = -0.289) in either direction. Polling can fail in unexpected ways and when it misses the actual results, this error margin is usually within the difference between the two candidates’ number of votes. This means that if the popular vote determined the president, then polls would more often than not be a poor predictor at the national level, possibly due to the nature of polls themselves reaching more Democratic voters than Republican voters in general. This subject is under debate, where finding a good solution of reaching a wider group of people that don’t necessarily answer polls may not be a true solution. Plotting these error values dating back to 1936, we can determine the 95% confidence interval to account for a 3.3%-5.7% absolute error margin during any given election cycle. 

<img src="images/usa margin of error by party.png?raw=true"/>
<img src="images/usa absolute error margin.png?raw=true"/>


The 2020 election cycle is still being finalized after more than two weeks, where several states have not yet certified the results due to mail in ballots that seem to skew towards democratic voters. With the dataset of general election polls available on 538’s website, I wanted to see for myself how far off the state polls were from the actual results. By taking the sum of all polls rated C+ or better per state of Biden vs Trump since Biden declared candidacy in April 2019, I created some choropleth maps showing how both Democrats underperformed their polls and Republicans outperformed their polls as well. Overall, the actual results seemed “more red” than the polls- this 2020 election cycle had a combination of Democrats nationally underperforming by 3.06%, and the Republicans overperforming by 1.27%. Taking the absolute magnitude, this cycle had a 4.33% margin of error, which falls within the previously calculated 95% confidence interval for error margin during an election cycle. A few notable examples include Republicans beating polls by 11% in the battleground state of Michigan, Democrats underperforming in the split-district state of Nebraska by 13%, and a combination of Democrat underperformance and Republican overperformance with close races in Georgia, North Carolina, and Pennsylvania.


<img src="images/usa results.png?raw=true"/>
<img src="images/usa polls.png?raw=true"/>
<img src="images/usa democrat underperform.png?raw=true"/>
<img src="images/usa republican overperform.png?raw=true"/>

In conclusion, it’s important to have good granular data when predicting elections as a whole- lots of polls done at the national level and rated D+ or worse by FiveThirtyEight were dropped before including in analysis. There also were *zero* state level polls done in Rhode Island, showing that there may be a limited reach of all polling organizations across the board. While the 5% expected variance in every election cycle may be an artifact of national polling; often getting better granularity at the state level is both a better slice of people who live in a given state and narrowing choices to only Trump or Biden nearer to election time would reduce error taken into account when analyzing polling data. 

---
<p style="font-size:11px">Page template forked from <a href="https://github.com/evanca/quick-portfolio">evanca</a></p>
<!-- Remove above link if you don't want to attibute -->
