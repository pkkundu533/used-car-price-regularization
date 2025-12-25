## Regularisation in Linear Models — Applied Study

This repository contains an applied analysis of linear regression,
Ridge, and Lasso regularisation on a real-world used-car pricing dataset
(~15k records).

### Goal
Evaluate when regularisation meaningfully improves model behaviour,
rather than assuming additional complexity improves results.

### Key Takeaways
- Strong preprocessing influenced results more than algorithm choice
- A well-prepared linear baseline already explained ~92% variance
- Ridge improved coefficient stability under multicollinearity
- Lasso did not eliminate features after effective feature engineering
- Regularisation improved robustness and trust more than accuracy

### Why this matters
In production ML systems, simplicity, stability, and explainability
often outweigh marginal metric gains from added complexity.

### Dataset
AutoScout used car listings (public dataset).
