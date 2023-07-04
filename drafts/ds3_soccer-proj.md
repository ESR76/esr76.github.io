---
layout: post
title: Passing and Team Success in Soccer
description: Our team of four used passing data to evaluate player and team success in soccer matches, as well as creating an interactive data visualization to view players in different positions.
---

#### Abstract
The use of data science in sports has exploded in recent years with teams and management in a variety of sports changing to a more data-driven decision making process in the hunt for glory. This project aims to continue that trend in soccer, and looks to analyze team success by examining their passing patterns and event potential over several years worth of data.

Please note - this is an abbreviated version of the results we published. To get a full view of the scope of this project, I recommend looking at the presented poster, as well as downloading and running the demo for this project by following the links at the bottom of the page.

##### Data
Our data came from [StatsBomb's Open Data package](https://github.com/statsbomb/open-data), a free package of a subset of StatsBomb's soccer data to encourage data analysis at all different levels of skill.

Much of our demo was based on exploratory and visual analysis we completed before building out our models: as such, our initial analysis was very important to what we developed with this project. 

After manually cleaning our JSON data into a Pandas DataFrame because of high and complex numbers of nested information, we ended up with a very sparse dataset for each "action" in the game of soccer. We also had to adjust several pieces of data because we were combining data of different leagues and time periods in order to compare players' passing records across all of the appearances we had access to. This also meant that we had to adjust some aspects of the data:
* Players' names needed to be individually changed to be consistent across all their leagues and appearances - mainly this was adjusting nicknames & last names for players who had been married.
* Men's and women's soccer matches needed to be carefully separated. Some teams had the same name for the men's and women's teams (ie. Manchester United, which did not distinguish between "Manchester United Men" and "Manchester United Women").
* Many players had different positions across different teams, so we treated each player in the context of each position they played. Sometimes this meant that our analysis ended up being time-based/team-based because a player had only played a certain position once in their career.
* Analyzing passing between two players who had never played together to analyze theoretical trades was difficult, so we used a combination of their pass history based on the two players' positions and the players' success passing from their absolute locations on the field.

Our data analysis covered several aspects of the game. We analyzed where shots were taken, how shots were taken across time in matches, how far goal keepers came out of their box, longer passing chains and different keys to success, and how players acted differently across different positions. These aspects all made it to our interactive demo, where participants could use this information to put together their favorite players in one team.


##### Models
After analyzing our data, we regarded a successful "pass" in 3 different ways for different models. 

1. Our first definition stated "success" was a continuation of possession and a failed "pass" was a turnover of possession. 
2. Our next definition was whether the pass led to a "successful" or "failure" next event, where we classed every event type in StatsBomb's database (ie. , ,) as a positive or negative event.
3. Our final definition was an extension of definition 2, where some follow-up events were classed as "neutral" instead of "successful" or "failure".

We looked into metrics that evaluated passes as a function of contributing directly to a goal or moving the ball up the field, but we found that those metrics did not represent the variety of different styles of play (for example, they may benefit a more attack-heavy style than a tiki-taka style). This definition of pass was used for our later model to determine how successful a team was.

Each of these 3 definitions were fed into a classifier via Sci-Kit Learn (after using Sci-Kit Learn's optimization package). 

##### Results Overview
After feeding the data through the model, we found some interesting results. The first two models had similar high F1 scores, and the first model broke the tie with a higher accuracy measure. However, both of these models heavily overpredicted success, relying on the imbalance in the dataset with many more successful events than failed events. In contrast, the third model had a lower F1 score and accuracy measure, but did predict more evenly across "successful", "failure", and "neutral" events.

With more time, we would've liked to include more individual player evaluation in our model and try to ensure a model that predicts variety in the different levels of success, while also maintaining the highest level of accuracy we found in the earlier models.

#### Full Results and Work
To view all of the results of our work and our more in-depth process, please read over our [poster](https://www.canva.com/design/DAE_GZZcC4s/534ixPVnTqEc9SkTeMDmJA/view?utm_content=DAE_GZZcC4s&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink) from the final showcase and our [demo code](https://github.com/gprasad125/soccerDemo) to view the interactive demo on a local machine.

<img src="/assets/images/soccer_2.JPG"
     alt="A photo of my team of 4 with our project poster."
     style="float: left; margin-right: 10px;" />

<img src="/assets/images/soccer_1.JPG"
     alt="A photo of most of the project cohort for the Data Science Student Society in those two quarters."
     style="float: right; margin-left: 10px;" />

*Two photos from the showcase, the first with my team for the project, and the second with the whole project cohort.*

