---
title: Time Series with Spline Based Models
author: ''
date: '2019-04-19'
slug: time-series-with-spline-based-models
categories: []
tags: []
---

In this post we are going to see how to use three spline based methods: *thin plate splines*, *multivariate adaptive regression splines*, and *generalized additive models* to model time series data. Moreover, we will look at three different ways of using each model. Since these are not time series models per se, we have some flexibility it terms of how we actually fit the models to our data.

### The Data

The data we will be using comes from the [CDC FluView](https://www.cdc.gov/flu/weekly/index.htm) which is a CDC website that has information on influenza in the United States. They also have [FluView Interactive](https://www.cdc.gov/flu/weekly/fluviewinteractive.htm), a web application that allows you to interact with flu related data as well as download data.

We will be focusing on the weekly number of influenza-like illnesses (ILI) reported in California from 2010 to 2019 by members of the US Outpatient Influenza-like Illness Surveillance Network (ILINet). You can download the data from the FluView Interactive website. However, I recommend using the `cdcfluview` R package which you can find on [CRAN](https://cran.r-project.org/web/packages/cdcfluview/index.html) or [GitHub](https://github.com/hrbrmstr/cdcfluview).

blah






