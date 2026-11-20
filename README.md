# econ3916-lab17-classification

# Classification: When 90% Accurate Is Worthless

## Objective
I fitted a logistic regression to simulated loan applications and chose its decision threshold by the cost of the two kinds of error, not by accuracy.

## Methodology
- Worked with 6,000 simulated loan applications with a default rate of 9.6%, where a rule that approves everyone is 90.4% accurate.
- Fitted a logistic regression. At the usual 0.5 threshold its accuracy was 90.4%, with 0 predicted defaults.
- Read the coefficients as log-odds and as odds ratios, and showed that one odds ratio (1.63 for one more prior default) means different changes in probability at different starting points.
- Traced precision and recall across six thresholds.
- Chose a threshold by minimising the expected cost of the two errors, using cross-validated probabilities on the training rows and pricing the result once on the test rows.
- Wrote a small function, `precision_recall_at()`, that gives a classifier's precision and recall at any threshold.

## Key Findings
- Accuracy hides the problem. The model matched the approve-everyone rule at 90.4% because it declined nobody and missed every default.
- The model did learn something. At lower thresholds its precision and recall are well above what ignoring the features would give.
- The cost-minimising threshold was 0.121, against a closed-form threshold of 0.118.
- Expected cost was 944 per applicant at the chosen threshold, against 1,147 at 0.5.
- At the closed-form threshold of 0.118, precision was 0.181 and recall was 0.477.
