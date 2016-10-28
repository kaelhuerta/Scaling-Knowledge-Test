---
title: Speed to send first candidate
authors:
- Kael Huerta
tags:
- knowledge
- jobs
- matching
- first-candidate
- glm
- splines
created_at: 2016-10-26 00:00:00
updated_at: 2016-10-28 02:31:30.203766
tldr: We compare the cancellation probability of a job in terms of the time it took
  our team to send the first candidate from the time the job was posted and the time
  it was claimed. We assess if it is worth speeding up the matching process.
---

**Contents**

[TOC]

### Main Result

This research suggests that within the first week after the job was claimed,
there is no gain in hurrying the first candidate sent. After a week we can see
how the probability of cancellation starts increasing.

<!-- Loading libraries  -->




```r
getwd()
```

```
## [1] "/Users/kael/toptal/knowledge-repo"
```





```
## Error in eval(expr, envir, enclos): object 'dataset' not found
```

```
## Error in eval(expr, envir, enclos): object 'dataset' not found
```


```
## bayesglm(formula = cancelled ~ bs(post.to.first, df = 10, Boundary.knots = c(0, 
##     31)), family = binomial(link = "logit"), data = ., prior.scale = rep(0.01, 
##     10), prior.df = 1)
##                                                         coef.est coef.se
## (Intercept)                                             -1.640    0.063 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))1  -0.007    0.019 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))2   0.023    0.046 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))3   0.009    0.026 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))4   0.001    0.023 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))5   0.001    0.025 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))6  -0.001    0.020 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))7   1.550    0.206 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))8   1.032    0.404 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))9   6.935    0.603 
## bs(post.to.first, df = 10, Boundary.knots = c(0, 31))10  0.001    0.010 
## ---
## n = 2715, k = 11
## residual deviance = 2688.2, null deviance = 3165.0 (difference = 476.8)
```


```
## bayesglm(formula = cancelled ~ bs(claim.to.first, df = 10, Boundary.knots = c(0, 
##     31)), family = binomial(link = "logit"), data = ., prior.scale = rep(0.03, 
##     10), prior.df = 1)
##                                                          coef.est coef.se
## (Intercept)                                              -3.086    0.111 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))1  -0.031    0.050 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))2   0.003    0.075 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))3   0.006    0.102 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))4  -0.032    0.104 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))5  -0.021    0.054 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))6  -0.004    0.077 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))7   0.045    0.065 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))8   3.566    0.596 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))9   7.669    0.877 
## bs(claim.to.first, df = 10, Boundary.knots = c(0, 31))10  0.011    0.032 
## ---
## n = 2261, k = 11
## residual deviance = 1010.4, null deviance = 1309.4 (difference = 299.0)
```
