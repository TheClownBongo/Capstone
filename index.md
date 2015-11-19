---
title       : Yelp Predict Business Rating
subtitle    : 
author      : The Clown Bongo
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

##  The
---

## Background and Models

The data comes from the Yelp Dataset Challenge. Out of the data sets, only the data on businesses and reviews for those buinesses were used.
The data was split into training and testing sets with a ratio of 60/40. 

Using the training set, classification support vector machines and random Forest models were derived. The businesses rating are from 1 to 5 with an increment of .5 that were treated as factors while building the models. 

The support vector machines model is a radial kernel C-Classification 10-fold cross-validation. The in-sample accuracy is 78.58% and in-sample error of 21.42%. The out-of sample accuracy is 78.46% and out-of-sample error of 21.54%. 

The random Forest model is a classification with 500 trees and number of variables tried at each split 3. The out-of-bag estimate is 20.12%. The in-sample accuracy is 98.43% and in-sample error of .57%. The out-of-sample accuracy is 79.14% and out-of-sample error of 20.86%.

---

## Plot of Actual Ratings Versus Predicted

The predicted rating of a business is obtained from a random Forest model.

<img src="assets/fig/read_data_plot-1.png" title="plot of chunk read_data_plot" alt="plot of chunk read_data_plot" style="display: block; margin: auto;" />

---

## Error Information on Testing Set

Support vector Machines

```
##             1 Star 1.5 Stars 2 Stars 2.5 Stars 3 Stars 3.5 Stars 4 Stars
## Sensitivity 88.48%    66.59%  66.58%    68.76%  72.00%    78.41%  78.57%
## Specificity 99.59%    99.56%  98.86%    97.51%   0.96%    93.65%  94.28%
##             4.5 Stars 5 Stars
## Sensitivity    80.18%  93.53%
## Specificity    96.61%  98.15%
```

Random Forest

```
##             1 Star 1.5 Stars 2 Stars 2.5 Stars 3 Stars 3.5 Stars 4 Stars
## Sensitivity 70.89%    76.46%  67.78%    74.01%  74.78%    78.66%  80.60%
## Specificity 99.91%    99.42%  98.79%    97.10%  96.04%    94.32%  94.56%
##             4.5 Stars 5 Stars
## Sensitivity    83.66%  87.98%
## Specificity    96.47%  99.29%
```

---

## Are Both Models Equivalent? Can They Be Improved?

The support vector machines and random Forest models provide pretty similar out-of sample errors, with an accuracy around 78-79%. The in-sample error for the support vector machines model is much larger than for the random Forest one but is consistent with the out-of sample error since it is a 10-fold cross-validation. By including more information like the field vote.useful and mining the text of the review for specific words like best and worst, one could weight more or less some reviews.






