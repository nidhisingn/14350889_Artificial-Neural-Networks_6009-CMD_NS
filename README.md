# 14350889_Artificial-Neural-Networks_6009-CMD_NS
This repository contains ANN project coding.
# Bank Marketing Classification using Artificial Neural Networks

This repository contains coursework for an Artificial Neural Networks application project based on the **Bank Marketing** dataset. The project investigates how artificial neural networks can be used to predict whether a bank customer will subscribe to a term deposit, and compares two development approaches:

- **Part A:** Human-guided ANN design
- **Part B:** GenAI-assisted ANN design

The project focuses not only on predictive performance, but also on **class imbalance**, **uncertainty analysis**, **confusion analysis**, and **critical comparison of model design choices**.

---

## Project Objective

The main objective of this project is to design, implement, evaluate, and critically compare ANN models for binary classification of term-deposit subscription outcomes.

The work was structured to answer two key questions:

1. How far can performance be improved through careful human-guided ANN design?
2. Can Generative AI provide useful support in model architecture and evaluation design without replacing human judgement?



## Dataset

The project uses the **Bank Marketing** dataset, a well-known binary classification dataset derived from direct telemarketing campaigns conducted by a Portuguese banking institution.

### Dataset characteristics
- **Rows:** 45,211
- **Variables:** 17
- **Target:** `y` (`yes` / `no`)
- **Task type:** Binary classification
- **Challenge:** Strong class imbalance

The target distribution is highly skewed, with many more `no` cases than `yes`, so the project uses **class-sensitive evaluation metrics** rather than relying only on accuracy.



## Preprocessing Pipeline

A shared preprocessing workflow was used for both Part A and Part B to ensure fair comparison.

### Key preprocessing steps
- initial data inspection
- duplicate and missing-value checks
- analysis of `unknown` categories in categorical variables
- special handling of the `pdays` feature
- target encoding
- train / validation / test split
- categorical encoding and numerical scaling

### Important feature engineering
The `pdays` variable required special treatment because the value `-1` represented **“not previously contacted”** rather than a true elapsed-day count.

To address this, two engineered features were created:
- `was_previously_contacted`
- `pdays_clean`

### Data split
The dataset was split using a **stratified 70/15/15** train-validation-test strategy to preserve class balance across subsets.

### Feature versions
Two modelling versions were created:
- **With duration**
- **Without duration**

This was done because `duration` is highly predictive, but it is only fully known after a call, which limits practical deployment in pre-contact scenarios.



## Part A — Human-Guided ANN Design

Part A was developed without Generative AI and followed a controlled progression from a simple baseline to a stronger regularised ANN.

### Models developed in Part A
1. **Single-Layer Perceptron (SLP)**  
   Simple neural baseline with sigmoid output

2. **Baseline MLP**  
   Architecture: `52 → 32 → 16 → 1`

3. **Improved MLP**  
   Architecture: `52 → 64 → Dropout(0.30) → 32 → Dropout(0.20) → 16 → 1`

### Key Part A design choices
- hidden-layer nonlinearity
- dropout regularisation
- class-weighted training
- early stopping
- class-sensitive evaluation

### Best Part A result
The **Improved MLP** was the strongest model in Part A and the strongest overall model in the project on the most important class-sensitive metrics.


## Part B — GenAI-Assisted ANN Design

Part B explored whether Generative AI could act as a useful decision-support tool for ANN design.

Generative AI was used to suggest:
- deeper ANN architectures
- dropout strategies
- Batch Normalization
- callback strategies
- broader evaluation methods

However, suggestions were **not accepted blindly**. They were critically filtered, modified, or rejected depending on whether they fit the dataset and the modelling objective.

### Final Part B model
The final GenAI-assisted model used the following architecture:

`Input → Dense(128, ReLU) → BatchNormalization → Dropout(0.30) → Dense(64, ReLU) → BatchNormalization → Dropout(0.25) → Dense(32, ReLU) → Dropout(0.15) → Dense(1, sigmoid)`

### Key Part B design choices
- deeper hidden-layer structure
- Batch Normalization
- staged dropout
- reduced learning rate
- EarlyStopping
- ReduceLROnPlateau
- class-weighted training



## Evaluation Strategy

Because the dataset is imbalanced, the models were evaluated using more than accuracy alone.

### Metrics used
- Accuracy
- Precision
- Recall
- F1-score
- Balanced Accuracy
- ROC-AUC
- PR-AUC

### Additional analysis
- confusion matrices
- false-positive / false-negative trade-off
- ambiguity analysis using a probability band of **0.40–0.60**

This helped assess not just performance, but also prediction reliability and decision-boundary uncertainty.



## Key Results

### Part A results
| Model | Accuracy | Precision | Recall | F1-score | Balanced Accuracy | ROC-AUC | PR-AUC |
| SLP | 0.9003 | 0.6430 | 0.3317 | 0.4376 | 0.6536 | 0.9036 | 0.5343 |
| Baseline MLP | 0.9024 | 0.6116 | 0.4527 | 0.5203 | 0.7073 | 0.9188 | 0.5737 |
| Improved MLP | 0.8408 | 0.4133 | 0.8625 | 0.5588 | 0.8502 | 0.9215 | 0.5947 |

### Part B result
| Model | Accuracy | Precision | Recall | F1-score | Balanced Accuracy | ROC-AUC | PR-AUC |
| Advanced MLP (GenAI-assisted) | 0.8259 | 0.3889 | 0.8562 | 0.5349 | 0.8390 | 0.9137 | 0.5578 |

### Final conclusion
Although the GenAI-assisted model expanded the design space and introduced useful ideas such as Batch Normalization and validation-guided callbacks, the **Improved MLP from Part A** performed best overall on the most meaningful class-sensitive metrics.


## Repository Structure

A typical structure for this project is:

'''text
├── Part_A/
│   └── NS_14350889_ANN_PART-A.ipynb
├── Part_B/
│   └── NS_14350889_ANN_PART-B.ipynb
├── Part_C/
│   └──NS_14350889_ANN_PART-C.ipynb 
├── Outputs/
│   ├── figures/
│   ├── tables/
│   └── saved_results/
├── README.md
└── requirements.txt
