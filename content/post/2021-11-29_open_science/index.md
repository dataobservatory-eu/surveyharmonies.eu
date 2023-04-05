---
title:  "Open Science"
subtitle:  "Open Science"
date:  2021-11-29T09:41:00+01:00
lastmod:  2021-11-29T09:41:00+01:00
draft:  true

authors:  ["daniel_antal"]

tags:  ["open science", "metadata", "FAIR data"]

summary:  ""

projects:  ""

links:
- icon: twitter
  icon_pack: fab
  name: "@GreenDealObs"
  url: https://twitter.com/GreenDealObs
- icon: fingerprint
  icon_pack: fas
  name: Authoritative data
  url: https://zenodo.org/communities/greendeal_observatory/
- icon: linkedin
  icon_pack: fab
  name: Join our collaboration community on LinkedIn
  url: https://www.linkedin.com/company/78556699

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



| Subject                       | Numbrer  | Datasets |
| :---                          |    :----:   | :---:  |
| [Environmental Protection](https://id.loc.gov/authorities/subjects/sh85044203.html)      |  2/2 | [Government Budget Allocations for R&D in Environment](https://zenodo.org/record/5658849#.YaT8GdDMLIU) [Environment's Share in Total Government Budget Allocations for R&D](https://zenodo.org/record/5661169#.YaT8PNDMLIU)  |
| [Climate change](https://id.loc.gov/authorities/subjects/sh85027037.html)                          |    1/[1](https://zenodo.org/search?page=1&size=20&q=keywords:%22Climate%20change%22)   | [Most Serious Global Problem: Climate Change (Percentage of European Individuals)](https://zenodo.org/record/5711962#.YaT_i9DMLIU) |

For [Climate change](https://id.loc.gov/authorities/subjects/sh85027037.html) subject, as recognized by the Library of Congress Subject Headings, with variations *Changes, Climatic*, *Changes in climate*, *Climate change*, *Climate change science*, *Climate changes*, *Climate variations*, *Climatic change*, *Climatic changes--Environmental aspects*, *Climatic fluctuations*, *Climatic variations*, *Global climate changes*, *Global climatic changes*, we find 265 datasets, but after close inspection, only 25 are tabular data in csv or xlsx files. 

In the case of [Environmental Protection](https://id.loc.gov/authorities/subjects/sh85044203.html) , also known as *Environmental quality management*, *Protection of environment* we only find two datasets, those of our Green Deal Data Observatory. 

There is something clearly not going allright here. Out of the  2154041 open documents, only 42487 are csv or xlsx tabular tables, yet before we started using them, seemingly nobody published data in these subjects.





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
