# The Bias-Variance Tradeoff: Choosing How Flexible a Model Should Be

## Objective
I wanted to find out how flexible a polynomial model should be by splitting its error into bias and variance and by choosing its degree with cross-validation.

## Methodology
- I built a simulated world with a known true curve and split the error of polynomial fits into bias squared and variance using 200 fresh samples at each of six degrees.
- I compared training error with error on 2,000 new points for degrees 1 to 15 and found the degree where the held-out error was lowest.
- I chose a degree with 5-fold cross-validation and looked at how much the error changed from fold to fold.
- I used nested cross-validation to check whether the smallest CV error is a fair estimate of the error on new data.
- I wrote a function called kfold_mse() that gives the k-fold CV error for any degree and number of folds and checked it with 10 folds.
- For the take-home Challenge I fit minimum-norm polynomials with degrees up to 991 and tracked their held-out error.

## Key Findings
- Variance went up from 0.0180 at degree 5 to 0.0994 at degree 15.
- The held-out error was lowest at degree 5.
- 5-fold CV chose degree 4 with a CV MSE of 0.1401.
- The nested CV estimate was 0.2070 so the smallest CV MSE was too low as an estimate of the error on new data.
- With 10 folds the CV MSE was 0.1409 for degree 4 and 0.1457 for degree 5 so 10 folds ranked the two degrees the same way as 5 folds.
- Past the interpolation point the held-out error went up to 8.08e+23 and then went down to 0.3185 at degree 991.
