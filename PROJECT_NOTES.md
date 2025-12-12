#  Project Notes – Learnings & Reflections

*(Fraud Detection with XGBoost)*

## 1. Why This Project

Fraud detection is not just a classification task—it is a **decision problem under uncertainty**.
In banking, every transaction requires balancing **risk, customer trust, and explainability** under time pressure.
The aim of this project was to explore how data and machine learning can **support better decisions**, rather than replace human judgment.




## 2. How I Think About Fraud

Fraud modelling is fundamentally about **trade-offs**:

* **False positives** create customer friction and long-term trust loss.
* **False negatives** create direct financial loss and regulatory exposure.

There is no universally “correct” threshold.
The right balance depends on **context, customer value, and risk appetite**.
This mindset shaped both my modelling choices and evaluation strategy.




## 3. Model Choice Mindset

I deliberately chose **XGBoost** for this project because:

* It performs exceptionally well on **tabular financial data**.
* It handles **class imbalance** effectively.
* It provides strong performance without sacrificing interpretability.

Rather than starting with complex architectures, I focused on:

* Understanding the **signal in the data**
* Validating assumptions
* Building a model that could be **trusted and explained**

> Complexity can always be added later. Understanding cannot.




## 4. Explainability — How I Think About SHAP

I use SHAP to make model decisions **transparent and auditable**.

A helpful analogy:

> **SHAP is like the bibliography of a book.**

* The **model** is the book.
* The **prediction** is the final conclusion.
* **SHAP** shows which “sources” (features) contributed to that conclusion, and by how much.

This allows:

* Global understanding of which features matter most
* Local explanations for individual transactions
* Decisions that can be **explained to auditors, regulators, and non-technical stakeholders**





## 5. Mistakes I Made & What I Learned

This project helped me identify and correct several early assumptions:

* Initially focusing too much on overall accuracy
* Underestimating the importance of **error costs**
* Learning that threshold selection is a **business decision**, not a purely technical one

Recognising and correcting these mistakes significantly improved both the model and my understanding of real-world fraud systems.





## 6. Banking Reality Notes

From a real-world banking perspective:

* Fraud is **rare**, but the cost of mistakes is high.
* Models do not make decisions—**people do**.
* Explainability is not optional; it is a **regulatory requirement**.
* The most valuable models are those that decision-makers **trust and understand**.




## 7. How I Would Improve This in Production

If this model were deployed in a live environment, I would focus on:

* Threshold tuning based on customer segments
* Monitoring data drift and model performance
* Human-in-the-loop review for edge cases
* Real-time dashboards for fraud monitoring
* API deployment and alerting mechanisms





## 8. Final Reflection

This project shifted how I think about data science in finance.
I no longer see models as prediction engines, but as **decision-support tools**.

> The goal is not perfect accuracy.
> The goal is better decisions under uncertainty.





### Author

**Emine Ceran**

Financial Data Science Journey

GitHub: [https://github.com/ebceran](https://github.com/ebceran)

LinkedIn: [https://www.linkedin.com/in/emine-ceran-03b26159/](https://www.linkedin.com/in/emine-ceran-03b26159/)


