## Can we beat a FastAI model in classification accuracy, by using a RandomForestClassifier?

For my unit 2 project, I wanted to use machine learning in order to predict the feature of a scientific model, as the part of data science that interests me the most is being able to make data-driven predictions based on its known intrinsic properties. Browsing through gold-rated datasets on Kaggle, I eventually found an astronomy dataset whose goal was to find potential planets outside of our solar system by Threshold Crossing Events, or according to Simple Wikipedia: “periodic dimming caused by extrasolar planets which cross in front of their host star”, and log these events captured by the Kepler Space Telescope. These events yield Objects of Interest (KOI), which are then inputted into a piece of software called the ‘Robovetter’ to see whether the event is a possible exoplanet or a false positive, and assigns the feature ‘koi_score’ based on this probability. While the score alone is able to correctly predict this, combining the score with the relevant data can yield better predictions of whether the exoplanet is ‘CONFIRMED’, A ‘CANDIDATE’, or a ‘FALSE POSITIVE’. 

Here I’m using an existing analysis by https://github.com/JamesMcGuigan/dataset-kepler with their FastAI model that takes ~15 minutes to train, and comparing its accuracy against simpler modeling methods we learned about in class using an 80/20 split between training and validation sets. Data cleaning methods were kept consistent between the two sets. Using the linear model as a baseline, this model correctly predicted 58% of the results, where the most error occurred in predicting an exoplanet was confirmed but was actually only a candidate. The FastAI implementation scored an 89% accuracy, where the largest source of error was predicting an exoplanet was a false positive but was actually a candidate.

<img src="images/1_fastai.png?raw=true"/>

<img src="images/2_rfc.png?raw=true"/>

<img src="images/3_linear.png?raw=true"/>

After running the linear model, I created a RandomForestClassifier pipeline which took the same input data, and was able to score a mean accuracy of 91%. This was done through changing the hyperparameters to use all 78 columns and traverse the maximum tree depth, which took some time to run but was still about 10 minutes faster than the FastAI model. Some previous tests seemed to have their accuracy cap out around 89% when limiting the column amounts to sqrt(n) and log2(n). Contradicting the FastAI model, the largest source of error showed on the RandomForestClassifier confusion matrix was incorrectly predicting a confirmed exoplanet when it would actually only be a candidate. 

Evaluating a feature importance graph for the dataset gave an unsurprising result- that ‘koi_score’ is the best predictor of identifying the target feature, as this column was evaluated by the Robovetter in order to properly classify these potential exoplanets. The next best feature is ‘koi_max_mult_ev’, which represents the maximum value of multiple samples within a single event, and seems to be an indicator to discern between an event being either a false positive or candidate. The grouping afterwards includes a couple of binary flags that indicate an anomaly associated with the captured event, which usually represents not being correlated to an exoplanet. 

<img src="images/4_featimp_score.png?raw=true"/>

A stretch goal I’m interested in doing more analysis on is the feature importance of the remaining variables when excluding the koi_score feature, as this was in the example’s notebooks of yielding 82% accuracy on the FastAI model only by using the score, fpflags features, and comments that were all onehot encoded. I was surprised to have my RandomForestClassifier still remain at 91% accuracy, and greatly overestimated how important the Robovetter’s score feature was in predicting accuracy than it actually performed.

<img src="images/5_featimp_flag.png?raw=true"/>

---
<p style="font-size:11px">Page template forked from <a href="https://github.com/evanca/quick-portfolio">evanca</a></p>
<!-- Remove above link if you don't want to attibute -->
