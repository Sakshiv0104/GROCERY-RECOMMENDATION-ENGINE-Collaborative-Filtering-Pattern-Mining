# GROCERY-RECOMMENDATION-ENGINE-Collaborative-Filtering-Pattern-Mining

# 🛒 Grocery Recommendation Engine: Collaborative Filtering & Pattern Mining

A grocery recommendation engine that suggests the **top 10 products** each customer is most likely to buy next, built with **user-based collaborative filtering** and **frequent pattern mining** on real transaction data.

> Team project completed as part of my Master of AI & Machine Learning at Adelaide University, with teammates Mukta and Eshrak.

---

## 📊 Results

Evaluated on **unseen transaction data**:

| Approach | Precision | Recall |
|---|---|---|
| **User-based Collaborative Filtering** | **0.40** | **0.21** |
| Hybrid (CF + association-rule boost) | 0.32 | 0.12 |

**Key finding:** pure collaborative filtering gave the most accurate, personalised recommendations. Adding mined rules on top actually reduced precision and recall, so we recommended CF as the main recommendation system.

---

## 🧠 Approach

### 1. Data & EDA
- Read and cleaned customer transaction data
- Exploratory analysis of transactions and purchasing behaviour
- Selected and processed customer baskets for modelling

### 2. Frequent Pattern Mining
- Mined association rules with **Apriori**, tuning **support, confidence and lift**
- Evaluated rules on **unseen test data** to make sure they generalise, not just fit the training set
- Compared rule quality, antecedent and consequent lengths, and total rule counts using summary tables
- Experimented with **FP-Growth** (near-identical results, slightly faster) and **ECLAT** (via `pyfim`)

### 3. Collaborative Filtering
- User-based CF generating top-10 product recommendations per customer
- Compared pure CF against a hybrid approach that boosts rule-backed items
- Analysed **execution time** of CF with and without mined patterns

### 4. Deployment Thinking
- Designed to run online and in-store with light compute, and to scale as customer history grows
- **Cold start:** recommend popular or same-category items until enough purchase history exists
- **Maintenance:** retrain regularly, retire outdated rules, and monitor precision and recall

---

## 🙋‍♀️ My Contributions

I led **Task 1: Frequent Pattern Mining**, and contributed across coding and reporting:

**Code**
- Data reading, transaction EDA, and basket selection and processing
- Association rule methodology: tuning parameters to improve generalisation, implementation and hyperparameter tuning
- Results tables and plots, including the support–confidence rule count table and sample rules
- Execution-time analysis of collaborative filtering with and without patterns
- Integrating all code into a single end-to-end notebook

**Experiments**
- FP-Growth and ECLAT comparisons. `pyECLAT` wouldn't install, so I found and used `pyfim` instead.

**Report**
- Full Frequent Pattern Mining method section, and the results discussion on parameter selection, generalisation and rule confidence on unseen data

---

## 💡 What I Learned

- **Generalisation matters:** rules that look good on training data can fail on unseen data, so tuning has to be judged on test data.
- **Tuning support, confidence and lift is a balancing act:** systematic summary tables made those choices clear instead of guesswork.
- **Simpler can win:** the hybrid approach sounded better on paper, but pure CF performed best when measured properly.

---

## 🔮 Future Work

- Add customer browsing history
- Try content-based recommendations using product features
- Use FP-Growth for faster pattern mining at scale
- Smarter blending of rule-backed items into CF recommendations

---

## 🛠️ Tech Stack

`Python` · `Pandas` · `Collaborative Filtering` · `Apriori` · `FP-Growth` · `ECLAT (pyfim)` · `Jupyter Notebook`

---

## ▶️ How to Run

1. Clone the repo
2. Open `GROCERY RECOMMENDATION ENGINE Collaborative Filtering & Pattern Mining.ipynb` in Jupyter
3. Run the cells in order. Each section has its inputs and outputs included.
