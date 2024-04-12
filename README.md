# DS-recruitment-challenge

## Data Analysis

This dataset presents some challenges for analysis due to the limited number of columns provided. Having an additional column explaining the reasons for returns would be highly valuable. However, the available data still contains important information that can be extracted.

### Key Insights

**Price:** The price point of $69.95 seems to have the highest rate of returns.

**Date:** June tends to experience the highest rate of returns due to a combination of factors:

- Events like Father's Day and graduation ceremonies prompt increased gift purchases, often resulting in recipients receiving items that don't meet their needs or preferences.
- Major online sales events like Prime Day occur in June, leading customers to take advantage of discounts without physically seeing or trying items, which can result in higher return rates due to discrepancies between expectations and reality upon receipt.
- During July and August, many people are on vacation, typically decreasing the number of returns as reduced availability and focus on leisure activities mean fewer individuals are engaging in shopping or returning items.

Consequently, June stands out as the month with the highest return rates, influenced by both seasonal events and online shopping behaviors.

**Product Type:** The product with model group 3162564956579801398 might be seeing more returns due to potential issues like quality control problems, misleading product descriptions, or tough competition in the market. However, these are just speculations for now, and more details from the company would be needed to confirm the reasons.

## Model Building

To predict whether a product will be returned by a customer, a classification model was built.

### Data Preprocessing

The classes were extremely imbalanced, with the minority class (1) representing when a customer returned a package. To address this, the minority class was upscaled.

### Model Selection

Two different models were tried: RandomForestClassifier and XGBClassifier. The RandomForestClassifier provided the best results, so it was selected for further analysis.

### Models Performance Evaluation

#### RandomForestClassifier (chosen one)

|        | precision | recall | f1-score | support |
|--------|-----------|--------|----------|---------|
| 0      |   0.98    |  0.99  |   0.99   | 338493  |
| 1      |   0.76    |  0.56  |   0.64   |  13485  |
| accuracy |          |        |   0.98   | 351978  |
| macro avg |   0.87  |  0.78  |   0.81   | 351978  |
| weighted avg | 0.97 |  0.98  |   0.97   | 351978  |

roc_auc_score = 0.9444277204453706

#### XGBClassifier

|        | precision | recall | f1-score | support |
|--------|-----------|--------|----------|---------|
| 0      |   0.98    |  0.85  |   0.91   | 338493  |
| 1      |   0.12    |  0.52  |   0.19   |  13485  |
| accuracy |          |        |   0.83   | 351978  |
| macro avg |   0.55  |  0.68  |   0.55   | 351978  |
| weighted avg | 0.94 |  0.83  |   0.88   | 351978  |

This model is performing reasonably well and manages to predict correctly whether a product will be returned or not for the majority of cases. The RandomForestClassifier outperformed the XGBClassifier on this dataset.

## Future Improvements

For further improvement, better data would be required:

- An additional column describing the reasons for returns would help the algorithm predict future customer behavior more efficiently.
- Access to product descriptions and reviews could enhance the model's performance, as it could study different reviews and descriptions that lead to returns.

```