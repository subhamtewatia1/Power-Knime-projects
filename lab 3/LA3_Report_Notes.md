# Lab Assessment 3 – Report notes (paste into RollNo_LA3_Report.pdf)

All values below were produced by the workflow `RollNo_LA3` (KNIME 5.12, Titanic data, seed 42).

## Screenshot checklist (one screenshot + one-line caption each)

| # | Open this | Caption |
|---|-----------|---------|
| 1 | Whole workflow canvas | Workflow with four annotated sections: Prepare, Explore, Model, Report. |
| 2 | CSV Reader → output table | titanic.csv imported: 891 rows × 12 columns. |
| 3 | Statistics View (#2) → view | Missing values: Age 177, Cabin 687, Embarked 2. |
| 4 | Prepare Data component → output table | Prepared table: 891 rows × 10 columns, no missing values (Age = 28, Embarked = S). |
| 5 | Row Filter → output | 1st-class passengers only: 216 rows. |
| 6 | GroupBy → output | Survival rate: female 0.742 (314), male 0.189 (577). |
| 7 | Statistics (#8) → output | Age mean 29.36 (min 0.42, max 80); Fare mean 32.20 (min 0, max 512.33). |
| 8 | Bar Chart | Average Survived by Sex: female 0.74, male 0.19. |
| 9 | Histogram | Age distribution; tall bar near 28 from median filling. |
| 10 | Box Plot | Fare by Sex; many high-fare outliers up to 512.33. |
| 11 | Scatter Plot | Age vs Fare; survivors (green) more common at higher fares. |
| 12 | Linear Correlation → output | Survived vs Pclass −0.338, Fare +0.257 (strongest). |
| 13 | Table Partitioner → both outputs | 70/30 stratified split: 623 training / 268 test rows. |
| 14 | Decision Tree View | First split is Sex. |
| 15 | Scorer (#19) → confusion matrix | Min 5 records/node: accuracy 78.7% (211 / 268). |
| 16 | Scorer (#23) + Learner (#21) view | Min 20 records/node: accuracy 79.5%, tree shrinks from 25 to 10 leaves. |
| 17 | Data folder / Excel file | LA3_Report.xlsx with 3 sheets; Predictions.csv with 268 rows. |
| 18 | Canvas after Reset all → Execute all | Whole workflow re-runs with one click; every node green. |

## Confusion matrix (min 5 records per node, test data)

| Actual \ Predicted | No | Yes |
|---|---|---|
| No  | 143 | 22 |
| Yes | 35  | 68 |

Accuracy = (143 + 68) / 268 = 78.7 %. Cohen's kappa 0.54.
Min 20 records per node: 145 / 20 / 35 / 68 → 79.5 %.

## Two rules from the tree (training data counts)

1. **IF Sex = female AND Pclass ≤ 2.5 (1st or 2nd class) THEN Survived = Yes**: 115 of 120 survived (95.8 %).
2. **IF Sex = male AND Age > 13 AND Fare ≤ 26.27 THEN Survived = No**: 250 of 275 died (90.9 %).

(Also: IF Sex = male AND Age ≤ 13 THEN Yes, 18 of 33.)

## Three insights

1. Women survived far more often than men (74.2 % vs 18.9 %), and Sex is the first split of the decision tree.
2. Class and money mattered: 1st-class passengers survived at 63.0 % against 38.4 % overall. Pclass (−0.34) and Fare (+0.26) are the strongest correlations with survival.
3. The tree predicts about 79 % of unseen passengers correctly (a model that always says "No" scores about 62 %). The simpler tree with 20 records per node is just as accurate (79.5 %) with 10 leaves instead of 25, so it is easier to read.

## Viva quick answers

- **Median for Age, drop Cabin:** Age is only 20 % missing, and the median (28) is robust to old outliers. Cabin is 77 % missing, so filling it would invent most of the column.
- **Drop PassengerId and Survived:** Survived is the answer in numeric form (it would give about 100 % accuracy). PassengerId is just a row number.
- **70/30 split:** train on 70 % and test on the 30 % the tree has never seen. Stratified sampling keeps the Yes/No ratio; seed 42 makes the split repeatable.
- **Confusion matrix:** rows are actual, columns are predicted, and the diagonal holds the correct predictions. Accuracy = correct ÷ total.

## Note
The "Data Explorer" node is not installed in this KNIME. The **Statistics View** node (#2) is used instead to read the missing values per column. The Color Manager used is the classic one (KNIME 5.12 marks it "deprecated", but it works and the charts use its colours).
