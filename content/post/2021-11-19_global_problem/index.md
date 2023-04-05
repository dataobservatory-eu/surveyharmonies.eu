---
title:  "100,000 Opinions on the Most Pressing Global Problem"
subtitle:  "Which of the following do you consider to be the single most serious problem facing the world as a whole?"
date:  2021-11-25T09:41:00+01:00
lastmod:  2021-11-25T09:41:00+01:00
draft:  false

authors:  ["daniel_antal"]

tags:  ["survey harmonization","data-as-service", "retroharmonize", "climate awareness", "Europe"]

summary:  "Imagine if you could compare data easily from surveys taken about climate change from all European countries, maybe even from other continents, from different years? If you could work with a sample of not only n=1000, n=4000, or n=10,000 but n=100,000? What type of granularity it would give you about the perception of climate change or supported policy measures?  That is exactly what our survey harmonization software allows for you to do."

links:
- icon: twitter
  icon_pack: fab
  name: "@GreenDealObs"
  url: https://twitter.com/GreenDealObs
- icon: code
  icon_pack: fas
  name: Code & Tutorials
  url: https://retroharmonize.dataobservatory.eu/
- icon: linkedin
  icon_pack: fab
  name: Join our collaboration community on LinkedIn
  url: https://www.linkedin.com/company/78556699
  
projects:  ""

# Featured image
image:
  # Caption (optional)
  caption:  ""

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point:  "Center"

  # Show image only in page previews?
  preview_only:  true

---

<td style="text-align: center;">{{< figure src="/img/blogposts_2021/global_problem_1_climate_change_5_plots.png" caption="A reprezentative sample of n=100793 from 5 years on the most serious global problem. Get the tidy dataset from [our repository](https://zenodo.org/record/5711962#.YZ9fNHvMJRA) or API." numbered="false" >}}</td>

Imagine if you could compare data easily from surveys taken about climate change from all European countries, maybe even from other continents, from different years? If you could work with a sample of not only n=1000, n=4000, or n=10,000 but n=100,000? What type of granularity it would give you about the perception of climate change or supported policy measures?  That is exactly what our survey harmonization software allows for you to do.

You can use and verify our software: it is a perfectly documented, open source, peer-reviewed scientific software. But for most users, a bit too difficult to handle.  This is why we are building the Green Deal Data Observatory as a user-centered  API around the software.  The Green Deal Data Observatory is processing climate-change related data from variuos survey, sensory, satellite data sources, and places them into tidy, easy-to-import datasets and visualizations.

Survey harmonization means various social science, statistical and data processing steps to make data comparable and joinable from various questionnaire answers taken in different countries, languages, and years. To demonstrate the power of retrospective survey harmonization, we have made an indicator, visualizations and a data animation from more than a hundred nationally representative surveys, which asked more than 137,000 Europeans about what they considered to be the single most serious problem facing the world as a whole?

![](/media/gif/global_problem_1_climate_change_800.gif)

Survey data harmonization refers to procedures that improve the data comparability or the possibility to make policy or scientific comparisons between data from surveys conducted in different countries or in different years. Our [retroharmonize](https://retroharmonize.dataobservatory.eu/) software helps this tedious, laborous, difficult data processing task. 

The result is stunning compared to a survey of 1000, 4000 or even 10,000 people.  In this video we have harmonized the answers from more than 137,000 Europeans surveyed in more than 20 languages. As you can see in the data animation, people got more and more concerned about climate change... until Covid struck.

Our data shows that more urban and higher educated people tend to be more and more concerned about climate change. Concern is higher and higher as younger and younger people are asked. (Our data source, the Eurobaromter survey is asking Europeans from the age of 15.)

There are huge national differences in Europe: people in the countries that we defined as Nordic (Scandinavia and Finland) are much more serious about climate change than the rest of the continent. It also matters when was the question asked: between 2013-2019 anxiety over the climate has been growing rapidly, but it peaked in 2019.  In 2020, the Covid pandemic has altered the problem map of the European population, with ‘infectious diseases’ other important global problems. But apart from the time of asking the question, and the place of asking, there are important patterns emerging all over Europe which are shared regardless of the time and place.


<td style="text-align: center;">{{< figure src="/img/blogposts_2021/CART_global_problem_1_climate_change.png" caption="Our classification tree model shows what factors play an important role in determining if somebody believes that climate change is the most important global problem." numbered="false" >}}</td>

People with no formal education rarely think that climate change is the most important global problem. People with secondary school education care less than people with tertiary education, and people with tertiary education or a bachelor's degree care less than people who have a university degree or who are committed to life-long learning. This effect is further emphasized by level of urbanization: the more urbanized are the respondents, the more likely they think that climate change is the single most important problem facing humanity. (Urban people tend to have higher education levels, too.)

Another important factor is age: the younger the respondent, the more likely to believe that climate change is the single most important problem.

One takeaway is that generally, people's climate awareness is rising: Europeans tend to be more urbanized and more educated, and this works in favor of recognizing this problem.  The coming younger generations are also more aware of climate change. Yet, as Covid-19 shows, a global trauma can alter the picture quickly.

Using the [implemented machine learning](https://christophm.github.io/interpretable-ml-book/) R software package of Christoph Molnar, we calculated the importance of various socio-demography variables in predicting who will think that climate change is the most important problem facing us.

<td style="text-align: center;">{{< figure src="/img/blogposts_2021/importance_global_problem_1_climate_change.png" caption="Out of the variables we investigated, time spent in education is the most important factor contributing to climate awareness, closely followed by the time when the question was asked." numbered="false" >}}</td>

The importance of age, time, and even the time spent in education (age of leaving formal education) show that there is very significant change over time. Unfortunately, this change is not monotonous, until 2019 climate awareness was growing by this indicator, then it declined due to Covid.

If you would ask a European citizen about the most important global problem today, the following decision tree would help guessing if she or he would reply "climate change". 

<td style="text-align: center;">{{< figure src="/img/blogposts_2021/CART_global_problem_1_climate_change.png" caption="Our classification tree model shows what factors play an important role in determining if somebody believes that climate change is the most important global problem." numbered="false" >}}</td>

The education level, the age, and the question of asking are very important variables, and so is the fact if the respondent has at least one child.  Interestingly, parents are less likely to be concerned about climate change then other people. In other words, the children are more concerned than their parents. 

## Get our data

You can always rely on our API to import directly the latest, best data, but if you want to be sure, you can use our [regular backups](https://zenodo.org/record/5711962#.YZ9fNHvMJRA) on Zenodo. Zenodo is an open science repository managed by CERN and supported by the European Union. On Zenodo, you can find an authoritative copy of our indicator (and its previous versions) with a digital object identifier, in this case, [10.5281/zenodo.5711962](https://doi.org/10.5281/zenodo.5711962). These datasets will be preserved for decades, and nobody can manipulate them. You cannot accidentally overwrite them, and we have no backdoor to modify them.

*Are you a data user? Give us some feedback! Shall we do some further automatic data enhancements with our datasets? Document with different metadata? Link more information for business, policy, or academic use? Please  give us any [feedback](https://reprex.nl/#contact)!*
