---
title:  "Economic and Environment Impact Analysis, Automated for Data-as-Service"
subtitle:  "Our new open source release will help with automated economic impact and environmental impact analysis."
date:  2021-06-03T16:00:00
lastmod:  2022-08-30T13:01:00+02:00
draft:  false

doi: 10.5281/zenodo.6033771

authors:  ["Daniel Antal"]

tags:  
 - Open data
 - Open science
 - iotables
 - Economic Impact Analysis
 - Enviromental Impact Analysis

summary:  "rOpenGov, Reprex, and other open collaboration partners teamed up to build on our expertise of open source statistical software development further: we want to create a technologically and financially feasible data-as-service to put our reproducible research products into wider user for the business analyst, scientific researcher and evidence-based policy design communities. Our new release will help with automated economic impact and environmental impact analysis."

projects:  
 - Eviota

links:
- icon: twitter
  icon_pack: fab
  name: "@GreenDealObs"
  url: https://twitter.com/GreenDealObs
- icon: code
  icon_pack: fas
  name: Code & Tutorials
  url: https://iotables.dataobservatory.eu/
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
  caption:  ""
  focal_point:  "Center"
  preview_only:  true

categories:
- R-bloggers
---

We have released a new version of
[iotables](https://iotables.dataobservatory.eu/) as part of the
[rOpenGov](http://ropengov.org/) project. The package, as the name
suggests, works with European symmetric input-output tables (SIOTs).
SIOTs are among the most complex governmental statistical products. They
show how each country’s 64 agricultural, industrial, service, and
sometimes household sectors relate to each other. They are estimated
from various components of the GDP, tax collection, at least every five
years.

{{% callout note %}}
This code tutorial is not outdated, but the [iotables](https://iotables.dataobservatory.eu/) R package has a new release with more environmental impact analysis featues.
{{% /callout %}}

{{< spoiler text="Click to expand table of contents of the post" >}}
{{<toc>}}
{{< /spoiler >}}

SIOTs offer great value to policy-makers and analysts to make more than
educated guesses on how a million euros, pounds or Czech korunas spent
on a certain sector will impact other sectors of the economy, employment
or GDP. What happens when a bank starts to give new loans and advertise
them? How is an increase in economic activity going to affect the amount
of wages paid and and where will consumers most likely spend their
wages? As the national economies begin to reopen after COVID-19 pandemic
lockdowns, is to utilize SIOTs to calculate direct and indirect
employment effects or value added effects of government grant programs
to sectors such as cultural and creative industries or actors such as
venues for performing arts, movie theaters, bars and restaurants.

Making such calculations requires a bit of matrix algebra, and
understanding of input-output economics, direct, indirect effects, and
multipliers. Economists, grant designers, policy makers have those
skills, but until now, such calculations were either made in cumbersome
Excel sheets, or proprietary software, as the key to these calculations
is to keep vectors and matrices, which have at least one dimension of
64, perfectly aligned. We made this process reproducible with
[iotables](https://iotables.dataobservatory.eu/) and
[eurostat](https://CRAN.R-project.org/package=eurostat) on
[rOpenGov](http://ropengov.org/)

{{< figure src="/img/package_screenshots/iotables_045.png" caption="Our iotables package creates direct, indirect effects and multipliers programatically. Our observatory will make those indicators available for all European countries." numbered="true" >}}

## Accessing and tidying the data programmatically

The iotables package is in a way an extension to the *eurostat* R
package, which provides a programmatic access to the
[Eurostat](https://ec.europa.eu/eurostat) data warehouse. The reason for
releasing a new package is that working with SIOTs requires plenty of
meticulous data wrangling based on various *metadata* sources, apart
from actually accessing the *data* itself. When working with matrix
equations, the bar is higher than with tidy data. Not only your rows and
columns must match, but their ordering must strictly conform the
quadrants of the a matrix system, including the connecting trade or tax
matrices.

When you download a country’s SIOT table, you receive a long form data
frame, a very-very long one, which contains the matrix values and their
labels like this:

    ## Table naio_10_cp1700 cached at C:\Users\...\Temp\RtmpGQF4gr/eurostat/naio_10_cp1700_date_code_FF.rds

    # we save it for further reference here 
    saveRDS(naio_10_cp1700, "not_included/naio_10_cp1700_date_code_FF.rds")

    # should you need to retrieve the large tempfiles, they are in 
    dir (file.path(tempdir(), "eurostat"))

    dplyr::slice_head(naio_10_cp1700, n:  5)

    ## # A tibble: 5 x 7
    ##   unit    stk_flow induse  prod_na geo       time        values
    ##   <chr>   <chr>    <chr>   <chr>   <chr>     <date>       <dbl>
    ## 1 MIO_EUR DOM      CPA_A01 B1G     EA19      2019-01-01 141873.
    ## 2 MIO_EUR DOM      CPA_A01 B1G     EU27_2020 2019-01-01 174976.
    ## 3 MIO_EUR DOM      CPA_A01 B1G     EU28      2019-01-01 187814.
    ## 4 MIO_EUR DOM      CPA_A01 B2A3G   EA19      2019-01-01      0 
    ## 5 MIO_EUR DOM      CPA_A01 B2A3G   EU27_2020 2019-01-01      0

The metadata reads like this: the units are in millions of euros, we are
analyzing domestic flows, and the national account items `B1-B2` for the
industry `A01`. The information of a 64x64 matrix (the SIOT) and its
connecting matrices, such as taxes, or employment, or *C**O*<sub>2</sub>
emissions, must be placed exactly in one correct ordering of columns and
rows. Every single data wrangling error will usually lead in an error
(the matrix equation has no solution), or, what is worse, in a very
difficult to trace algebraic error. Our package not only labels this
data meaningfully, but creates very tidy data frames that contain each
necessary matrix of vector with a key column.

iotables package contains the vocabularies (abbreviations and human
readable labels) of three statistical vocabularies: the so called
`COICOP` product codes, the `NACE` industry codes, and the vocabulary of
the `ESA2010` definition of national accounts (which is the government
equivalent of corporate accounting).

Our package currently solves all equations for direct, indirect effects,
multipliers and inter-industry linkages. Backward linkages show what
happens with the suppliers of an industry, such as catering or
advertising in the case of music festivals, if the festivals reopen. The
forward linkages show how much extra demand this creates for connecting
services that treat festivals as a ‘supplier’, such as cultural tourism.

## Example

    ## Downloading employment data from the Eurostat database.

    ## Table lfsq_egan22d cached at C:\Users\...\Temp\RtmpGQF4gr/eurostat/lfsq_egan22d_date_code_FF.rds

and match it with the latest structural information on from the
[Symmetric input-output table at basic prices (product by
product)](http://appsso.eurostat.ec.europa.eu/nui/show.do?wai=true&dataset=naio_10_cp1700)
Eurostat product. A quick look at the Eurostat website already shows
that there is a lot of work ahead to make the data look like an actual
Symmetric input-output table. Download it with `iotable_get()` which
does basic labelling and preprocessing on the raw Eurostat files.
Because of the size of the unfiltered dataset on Eurostat, the following
code may take several minutes to run.

    sk_io <-  iotable_get ( labelled_io_data:  NULL, 
                            source:  "naio_10_cp1700", geo:  "SK", 
                            year:  2015, unit:  "MIO_EUR", 
                            stk_flow:  "TOTAL",
                            labelling:  "iotables" )

    ## Reading cache file C:\Users\..\Temp\RtmpGQF4gr/eurostat/naio_10_cp1700_date_code_FF.rds

    ## Table  naio_10_cp1700  read from cache file:  C:\Users\..\Temp\RtmpGQF4gr/eurostat/naio_10_cp1700_date_code_FF.rds

    ## Saving 808 input-output tables into the temporary directory
    ## C:\Users\...\Temp\RtmpGQF4gr

    ## Saved the raw data of this table type in temporary directory C:\Users\...\Temp\RtmpGQF4gr/naio_10_cp1700.rds.

The `input_coefficient_matrix_create()` creates the input coefficient
matrix, which is used for most of the analytical functions.

*a*<sub>*i**j*</sub>:  *X*<sub>*i**j*</sub> / *x*<sub>*j*</sub>

It checks the correct ordering of columns, and furthermore it fills up 0
values with 0.000001 to avoid division with zero.

    input_coeff_matrix_sk <- input_coefficient_matrix_create(
      data_table:  sk_io
    )

    ## Columns and rows of real_estate_imputed_a, extraterriorial_organizations are all zeros and will be removed.

Then you can create the Leontieff-inverse, which contains all the
structural information about the relationships of 64x64 sectors of the
chosen country, in this case, Slovakia, ready for the main equations of
input-output economics.

    I_sk <- leontieff_inverse_create(input_coeff_matrix_sk)

And take out the primary inputs:

    primary_inputs_sk <- coefficient_matrix_create(
      data_table:  sk_io, 
      total:  'output', 
      return:  'primary_inputs')

    ## Columns and rows of real_estate_imputed_a, extraterriorial_organizations are all zeros and will be removed.

Now let’s see if there the government tries to stimulate the economy in
three sectors, agricultulre, car manufacturing, and R&D with a billion
euros. Direct effects measure the initial, direct impact of the change
in demand and supply for a product. When production goes up, it will
create demand in all supply industries (backward linkages) and create
opportunities in the industries that use the product themselves (forward
linkages.)

    direct_effects_create( primary_inputs_sk, I_sk ) %>%
      select ( all_of(c("iotables_row", "agriculture",
                        "motor_vechicles", "research_development"))) %>%
      filter (.data$iotables_row %in% c("gva_effect", "wages_salaries_effect", 
                                        "imports_effect", "output_effect"))

    ##            iotables_row agriculture motor_vechicles research_development
    ## 1        imports_effect   1.3684350       2.3028203            0.9764921
    ## 2 wages_salaries_effect   0.2713804       0.3183523            0.3828014
    ## 3            gva_effect   0.9669621       0.9790771            0.9669467
    ## 4         output_effect   2.2876287       3.9840251            2.2579634

Car manufacturing requires much imported components, so each extra
demand will create a large importing activity. The R&D will create a the
most local wages (and supports most jobs) because research is
job-intensive. As we can see, the effect on imports, wages, gross value
added (which will end up in the GDP) and output changes are very
different in these three sectors.

This is not the total effect, because some of the increased production
will translate into income, which in turn will be used to create further
demand in all parts of the domestic economy. The total effect is
characterized by multipliers.

Then solve for the multipliers:

    multipliers_sk <- input_multipliers_create( 
      primary_inputs_sk %>%
        filter (.data$iotables_row: = "gva"), I_sk ) 

And select a few industries:

    set.seed(12)
    multipliers_sk %>% 
      tidyr::pivot_longer ( -all_of("iotables_row"), 
                            names_to:  "industry", 
                            values_to:  "GVA_multiplier") %>%
      select (-all_of("iotables_row")) %>%
      arrange( -.data$GVA_multiplier) %>%
      dplyr::sample_n(8)

    ## # A tibble: 8 x 2
    ##   industry               GVA_multiplier
    ##   <chr>                           <dbl>
    ## 1 motor_vechicles                  7.81
    ## 2 wood_products                    2.27
    ## 3 mineral_products                 2.83
    ## 4 human_health                     1.53
    ## 5 post_courier                     2.23
    ## 6 sewage                           1.82
    ## 7 basic_metals                     4.16
    ## 8 real_estate_services_b           1.48

## Vignettes

The [Germany
1990](https://iotables.dataobservatory.eu/articles/germany_1990.html)
provides an introduction of input-output economics and re-creates the
examples of the [Eurostat Manual of Supply, Use and Input-Output
Tables](https://iotables.dataobservatory.eu/articles/germany_1990.html),
by Jörg Beutel (Eurostat Manual).

The [United Kingdom Input-Output Analytical Tables Daniel Antal, based
on the work edited by Richard
Wild](https://iotables.dataobservatory.eu/articles/united_kingdom_2010.html)
is a use case on how to correctly import data from outside Eurostat
(i.e., not with `eurostat::get_eurostat()`) and join it properly to a
SIOT. We also used this example to create unit tests of our functions
from a published, official government statistical release.

Finally, [Working With Eurostat
Data](https://iotables.dataobservatory.eu/articles/working_with_eurostat.html)
is a detailed use case of working with all the current functionalities
of the package by comparing two economies, Czechia and Slovakia and
guides you through a lot more examples than this short blogpost.

Our package was originally developed to calculate GVA and employment
effects for the Slovak music industry, and similar calculations for the
Hungarian film tax shelter. We can now programatically create
reproducible multipliers for all European economies in the [Digital
Music Observatory](https://music.dataobservatory.eu/), and create
further indicators for economic policy making in the [Economy Data
Observatory](https://economy.dataobservatory.eu/).

## Environmental Impact Analysis

Our package allows the calculation of various economic policy scenarios,
such as changing the VAT on meat or effects of re-opening music
festivals on aggregate demand, GDP, tax revenues, or employment. But
what about the *C**O*<sub>2</sub>, methane and other greenhouse gas
effects of the reopening festivals, or the increasing meat prices?

Technically our package can already calculate such effects, but to do
so, you have to carefully match further statistical vocabulary items
used by the European Environmental Agency about air pollutants and
greenhouse gases.

The last released version of *iotables* is Importing and Manipulating
Symmetric Input-Output Tables (Version 0.4.4). Zenodo.
[https://doi.org/10.5281/zenodo.4897472](https://zenodo.org/record/4897472),
but we are already  working on a new major release. (Download the {{< staticref "/media/bibliography/cite-iotables.bib" "newtab" >}}BibLaTeX entry{{< /staticref >}}.) In that release, we
are planning to build in the necessary vocabulary into the metadata
functions to increase the functionality of the package, and create new
indicators for our [Green Deal Data Observatory](https://greendeal.dataobservatory.eu/). This experimental
data observatory is creating new, high quality statistical indicators
from open governmental and open science data sources that has not seen
the daylight yet.

## rOpenGov and the EU Datathon Challenges

{{< figure src="/img/partners/rOpenGov-intro.png" caption="rOpenGov, Reprex, and other open collaboration partners teamed up to build on our expertise of open source statistical software development further: we want to create a technologically and financially feasible data-as-service to put our reproducible research products into wider user for the business analyst, scientific researcher and evidence-based policy design communities." numbered="true" >}}


[rOpenGov](http://ropengov.org/) is a community of open governmental
data and statistics developers with many packages that make programmatic
access and work with open data possible in the R language.
[Reprex](https://reprex.nl/) is a Dutch-startup that teamed up with
rOpenGov and other open collaboration partners to create a
technologically and financially feasible service to exploit reproducible
research products for the wider business, scientific and evidence-based
policy design community. Open data is a legal concept - it means that
you have the rigth to reuse the data, but often the reuse requires
significant programming and statistical know-how. We entered into the
annual [EU Datathon](https://reprex.nl/project/eu-datathon_2021/)
competition in all three challenges with our applications to not only
provide open-source software, but daily updated, validated, documented,
high-quality statistical indicators as open data in an open database.
Our [iotables](https://iotables.dataobservatory.eu/) package is one of
our many open-source building blocks to make open data more accessible
to all.

<!---
recruitment
-->

{{< spoiler text="Join our Green Deal Data Observatory collaboration!" >}}
*Join our open collaboration Green Deal Data Observatory team as a [data curator](/authors/curator), [developer](/authors/developer) or [business developer](/authors/team). More interested in economic policies, particularly computation antitrust, innovation and small enterprises? Check out our [Economy Music Observatory](https://economy.dataobservatory.eu/#contributors) team! Or your interest lies more in data governance, trustworthy AI and other digital market problems? Check out our [Digital Music Observatory](https://music.dataobservatory.eu/#contributors) team!*
{{< /spoiler >}}


