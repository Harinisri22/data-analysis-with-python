PCOS DIAGNOSIS


Polycystic Ovary Syndrome (PCOS) is a common endocrine disorder affecting 5–10% of reproductive-age women and is diagnosed using the Rotterdam criteria: at least two of hyperandrogenism, anovulation, or polycystic ovaries 
The dataset comprises 1,000 women aged 18–45, with key features including Age, BMI, Menstrual Irregularity (binary), Testosterone (ng/dL), Antral Follicle Count, and PCOS Diagnosis (0/1).
In this dataset, approximately 20% of participants are PCOS-positive, closely matching prevalence in many clinical studies 
Menstrual irregularity serves as a critical clinical clue reflective of ovulatory dysfunction, present in many PCOS cases 
Testosterone levels capture biochemical hyperandrogenism—an essential diagnostic aspect often evaluated in routine labs 
Antral follicle count quantifies ovarian morphology, where ≥12 small follicles is indicative in diagnosing PCOS via ultrasound 
With BMI included, the dataset allows assessment of metabolic associations, since obesity exacerbates PCOS risks and insulin resistance 

Logistic regression is a suitable modeling approach here, predicting binary PCOS outcomes from these variables 

The dataset is fully complete (no missing values), enabling straightforward training and evaluation.
Overall, this structured clinical dataset supports robust modeling to identify PCOS risk using well-established diagnostic markers, aligning with real-world clinical practices.



Key Insights & Comparison with Literature:

AGE
The age of the patient, ranging from 18 to 45 years.

BMI
The Body Mass Index, which is a measure of body fat based on height and weight, ranging from 18 to 35.
Each 1 kg/m² increase in BMI raises PCOS odds by ~15%. This aligns with studies showing higher BMI correlates with increased obesity-related PCOS risk—though in some populations (like India), the effect isn't as strong.

Menstrual Irregularity
A binary indicator showing whether the patient has irregular menstrual cycles (0 = No, 1 = Yes).
A hallmark of PCOS, irregular cycles here greatly raise the odds by ~4–5×—which mirrors findings in clinical settings where menstrual disturbance is a core diagnostic criterion 

Testosterone Level(ng/dL)
The level of testosterone in the patient's blood, an important hormonal indicator of PCOS, ranging from 20 to 100 ng/dL.
Every extra ng/dL of testosterone elevates odds by ~3%, meaning a 20 ng/dL increase could nearly double PCOS risk. Meta-analyses report mean testosterone of ~67 vs. 45 ng/dL in PCOS vs. non‑PCOS—and auROC ≈0.70 for testosterone as a diagnostic marker 

Antral Follicle Count (AFC)
The number of antral follicles detected during an ultrasound, ranging from 5 to 30, which helps in assessing ovarian reserve and PCOS presence.
Each extra follicle adds ~8% to the odds of PCOS. This makes biological sense, as higher AFC is part of PCOS’s ovarian morphology. The Rotterdam criteria set thresholds around ≥22 follicles per ovary as diagnostic 

Target Variable:
PCOS Diagnosis (binary): A binary indicator of whether the patient has been diagnosed with PCOS (0 = No, 1 = Yes), based on a combination of risk factors such as high BMI, testosterone levels, menstrual irregularity, and antral follicle count.

Logistic Regression Model (Example Output)
Using your variables—Age, BMI, Menstrual Irregularity (binary), Testosterone (ng/dL), Antral Follicle Count (AFC)—the model estimates:

Coefficients (B) and Odds Ratios (OR)

Predictor	B (coefficient)	OR = exp(B)	95% CI for OR	p-value
Intercept	–5.20	–	–	<0.01
BMI (per 1 kg/m²)	+0.14	1.15	1.00 – 1.32	0.05
Menstrual Irregularity	+1.50	4.48	1.10 – 18.24	0.04
Testosterone (per 1 ng/dL)	+0.03	1.03	1.00 – 1.05	0.03
AFC (per follicle)	+0.08	1.08	1.00 – 1.16	0.05

Logit Equation:
Logit(P)=−5.20+0.14⋅BMI+1.50⋅(Irregular=1)+0.03⋅T+0.08⋅AFC

Predicted Probability:
     P(PCOS=1)=exp(Logit(P))/1+exp(Logit(P))
📈 Model Accuracy
Accuracy: 89.5%
You correctly classified 179 out of 200 patients in the test set (both PCOS positive and negative).
​
 Confusion Matrix Breakdown
 Let’s decode the 2×2 results:
 |                   | **Predicted PCOS=1** | **Predicted PCOS=0** |
| ----------------- | -------------------- | -------------------- |
| **Actual PCOS=1** | TP = *insert*        | FN = *insert*        |
| **Actual PCOS=0** | FP = *insert*        | TN = *insert*        |

rue Positives (TP): correctly identified PCOS cases

False Negatives (FN): missed PCOS cases

False Positives (FP): wrongly flagged healthy as PCOS

True Negatives (TN): correctly identified healthy

✅ Summary
Accuracy = 89.5%, but deeper insight requires precision, recall, F1, specificity, and ROC-AUC.

Confusion matrix reveals where your model errs (misses vs false alarms).






