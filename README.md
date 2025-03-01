# A/B Testing Analysis

## Overview
This project analyzes an A/B test dataset to evaluate the effectiveness of a new feature in increasing user engagement. The analysis includes statistical hypothesis testing to determine if the observed difference in click-through rates (CTR) between the experiment and control groups is statistically significant.

## Dataset
- **File:** `ab_test_click_data.csv`
- **Rows:** 20,000
- **Columns:**
  - `user_id`: Unique identifier for each user
  - `click`: Binary indicator (1 = Clicked, 0 = Did not click)
  - `group`: Experiment (`exp`) or Control (`con`)
  - `timestamp`: Time of user interaction (50% missing values)

## Methods Used
### 1. **Click-Through Rate (CTR) Calculation**
The Click-Through Rate (CTR) for each group is calculated as:

\[ CTR = \frac{Total \ Clicks}{Total \ Users} \]

### 2. **Statistical Hypothesis Testing**
To determine whether the observed difference in CTR between the experiment and control groups is statistically significant, a **Z-test for proportions** is conducted.

#### **Null and Alternative Hypothesis**
- **Null Hypothesis (H₀):** There is no difference in CTR between the experiment and control groups.
- **Alternative Hypothesis (H₁):** The experiment group has a higher CTR than the control group.

### 3. **Z-test for Proportions**
The Z-score is calculated using the formula:

\[ Z = \frac{(p_1 - p_2)}{\sqrt{p(1 - p) \left( \frac{1}{n_1} + \frac{1}{n_2} \right) }} \]

Where:
- \( p_1 \) = CTR of the experiment group
- \( p_2 \) = CTR of the control group
- \( p \) = Pooled proportion, calculated as:
  
  \[ p = \frac{Total \ Clicks_{exp} + Total \ Clicks_{con}}{Total \ Users_{exp} + Total \ Users_{con}} \]

- \( n_1 \) = Sample size of the experiment group
- \( n_2 \) = Sample size of the control group

The p-value is obtained from the Z-score using the standard normal distribution.

### 4. **Confidence Interval Calculation**
To determine the range of plausible differences in CTR, a **95% Confidence Interval** is calculated as:

\[ (p_1 - p_2) \pm Z_{0.975} \times SE \]

where:
- \( SE \) = Standard Error, as computed in the Z-test formula.
- \( Z_{0.975} \) is the critical value for a 95% confidence level (≈1.96).

## Key Findings
- **Experiment Group CTR:** **61.16%**
- **Control Group CTR:** **19.89%**
- **Difference in CTR:** **41.27 percentage points**
- **Z-score:** **59.44**
- **P-value:** **0.000** (Highly significant)
- **95% Confidence Interval for CTR Difference:** **[39.91%, 42.63%]**

## Interpretation
- The experiment group demonstrated a **significantly higher click-through rate** compared to the control group.
- The **statistical significance** (p-value ≈ 0) confirms that the difference is **not due to random chance**.
- The **confidence interval does not include 0**, reinforcing the conclusion that the new feature positively impacts engagement.

## Next Steps
- Roll out the tested feature to all users to maximize engagement.
- Conduct further segmentation analysis to assess the impact on different user groups.
- Address missing values in the `timestamp` column for potential time-based insights.
- Explore long-term user behavior changes post-feature implementation.



