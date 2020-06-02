## Checklist for getting ready to pilot your experiment on AMT

### Have you started writing a pre-registration? 
_“Not a prison, but a plan”_
This can be quick — but we should write down somewhere what your main predictions are, and exactly how they are operationalized given the variables we are measuring. (OSF has some tools/templates)
How many participants do we plan to recruit in our first batch?
What are we measuring, and what are our most basic predictions?

### Various Stages of piloting
- **development**: piloting on ourselves, on our roommates/family members
  Before proceeding, we should ensure that our data are being saved correctly and we can run basic analyses on them
- **sandbox**: piloting on ourselves/colleagues, but hosted on sandbox version of AMT 
  Purpose of this phase is to: (1) make sure that the HIT works as expected embedded in the AMT iframe, (2) make sure that the HIT actually submits correctly when the participant finishes the last trial
- **small-batch**: pilot on small number of real AMT participants, e.g., n=6
  At this point make sure that you’ve caught bugs that might only arise when other people using other OS/devices try your task. More debugging as needed
  Run your analyses and make sure they are technically sound. We will not include these data points in our “production” target sample size. 
  iterationName can be something like: “mturktest0.”
  Increment as needed: “mturktest1,” “mturktest2,” etc.
- Have you written your pre-registration? If not, now would be a good time!
  Begin production run: “medium-batch”: run your experiment “for real” on a “medium-sized” sample, e.g., n=20
  Set iterationName to something sensible that you actually don’t mind using to document iterations of your experiment/project, e.g: “run1”
  Document this iteration in the README.md file of within proj/experiments in your repo. This is an example: https://github.com/cogtoolslab/graphical_conventions/blob/master/experiments/README.md
  Again, make sure that your analyses are technically sound (i.e., your plotting code, etc. works)
  Extend your analysis code to run any group-level statistics, but do not worry about interpreting “results” at this point.
- **completed-batch**: run your experiment “for real” by adding additional participants to reach your target sample size, e.g., n=50-100+, depending on goal of study
Keep same iterationName. 
  That’s it! Analyze your data, figure out what’s going on, and we’ll go from there!
