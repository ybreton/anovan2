# anovan2
*Improved wrapper for ANOVA statistics in MATLAB*

I've found that anovan is fine if you have table-like, single-long vector data, but my data are often arranged in a meaningful way--e.g.,
subjects along dim1, sessions along dim2, trials along dim3, etc. So I developed a wrapper for this, along with some useful ANOVA-related
functions.

* anovan2
   * [p,table,stats,terms,means,errors,Ns] = anovan2(Y,options)

   Conducts a (m x n x ... x p) ANOVA on the elements in Y, assuming the replicates are in the last dimension. 
   In addition to options available for anovan, takes 'covariate' parameter with a covariate matrix for ANCOVA.

* anovaEtaSq
   * [etaSq,partial] = anovaEtaSq(table)

   Calculates Eta squared, based on the table produced by anovan/anovan2.

* helmertContrasts
   * c = helmertContrasts(X,Y)
   
   Computes the Helmert contrasts of X on the dependent variable Y, contrasting group 1 vs the mean of groups 2 to the end, group 2 vs
   the mean of groups 3 to the end, etc. Optional arguments include familywise alpha for comparisons, whether or not to control for
   multiple comparisons, and whether or not to perform the one-way ANOVA first.

* leveneTest
   * [h,p,W] = leveneTest(X,G)
   
   Performs Levene's Test for Equality of Variances on the data in X, using the group designations in G. Returns the null hypothesis
   test (h), the p-value of that test (p), and the test statistic (W).
   
* AllCombinations
   * C = AllCombinations(A)
   
   Returns a matrix where each row provides one of each combination of the elements in cell array A.
