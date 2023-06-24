---
layout: post
title: Energy Cost and HVAC Optimization in Smart Buildings
description: Our team of four attempted to make predictions about future energy usage and cost in a building using energy data collected from UC San Diego's EBU-3B (the Computer Science & Engineering) building's smart-HVAC system.
---

#### Abstract
With mounting concerns around climate change and the rising costs of power, optimizing and reducing energy usage is a growing challenge. In order to provide insight on the opportunity for energy usage and cost optimization, our team used energy data from a building on UCSD’s campus and auxiliary information about UCSD’s pricing model for energy to build a model that predicts future energy spending and attempted reducing predicted energy spending by controlling two user-set variables.

Please note - this is an abbreviated version of the report we published as a result. The links to the full poster, report website, and code for this project can be found at the bottom of this page.

##### Data
Our data covered 15 rooms worth of data on floors 2, 3, and 4 of UC San Diego's EBU-3B (Computer Science) building with data from July 2017 to early January 2019. 

In order to clean the data to get it into a usable format for our project, we performed somewhat extensive data cleaning in a part of the data pipeline labeled `features` in our code. The major steps involved:

1. We separated our data into training and testing sets based on dates in the original datasets, where approximately 70% of the data is before August 1, 2018 and the rest is August 1, 2018 and onwards.
2. We floored timestamps in the dataset to the nearest hour and use medians to aggregate into buckets of that time, since the energy values range because of the 15 unidentified rooms in the dataset.
3. We imputed the training dataset with data based on the median for the value at that hour - this was the most stable trend that we found in the original data. We did not impute the testing dataset because we wanted to ensure that we were not evaluating the model on predictions of false values.

##### Models
We tried several different models with different configurations of the input data to predict energy usage for the building, including basic machine learning models such as a linear regressor and a decision tree regressor, Meta's open-source time-series model [Prophet](https://github.com/facebook/prophet), neural networks, and autoregression. Many of our attempts were limited by the time we had to train the model and errors we ran into given the complexity and many variables in our data.

In the end, the most predictable/re-creatable performance came from our decision tree model, and as such we ended up making final predictions using the decision tree.

##### Results Overview
We predicted future energy usage in UC San Diego's computer science building and scaled the numbers using data from UCSD's pricing plan to scale for cost.

The conclusions we came to were fairly inconclusive, as our analysis relied on pre-COVID data, and one of our initial concepts with this project was to examine how COVID and post-COVID changed energy needs. The major conclusion we did find however, is that the building was using a lot of energy on set-up and turn-off costs that could not be predicted by the model because they were too high, indicating that the best way to reduce future energy usage in this building is to work on how the system and users behave when they turn on the HVAC system for the day (ie. is there a way to ensure they're more aligned and do not use unnecessary energy in the process.)


#### Full Results and Work
To view all of the results of our work and our more in-depth process, please read over our [poster](https://www.canva.com/design/DAFZKQlLOLo/2ALw0oHRO8qrPj--Q-8huw/view?utm_content=DAFZKQlLOLo&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink) from the final showcase and our [website](https://xenonition.github.io/) associated with this project, which contains our final report. The [code](https://github.com/ESR76/Capstone-Brick-Modeling/tree/main) for our project is also publically visible, if you'd like to read over it there.



