## AI Usage Report

### 1. What tool did you use?
* **Tool Name:** Gemini 3.6 Flash

---

### 2. What prompt did you use?
The exact primary prompt submitted to the AI assistant was:

> *Software effort estimation in a familiar context: effort_dataset.xlsx contains 30 historical projects with records for frontend technology, backend technology, AdjFP (Adjusted Function Points), team experience, urgency, 15 COCOMO adjustment factors, and effort in person-months.*  
> *Task: estimate the effort for a new project with the following characteristic: Frontend: React, Backend: Flask, AdjFP: 100, Urgency: Low. Note that the business analyst (BA) is unable to provide any COCOMO adjustment factors at this stage of the project, and the client is requesting a preliminary estimate.*  
> *Discuss how these four analyses (varying the adjustment factors) can help assess project risk and establish upper and lower bounds for the analogy-based estimation.*  
> *Finally, show some walkthrough to use pure llm to make the estimation without providing any historical data and find a way to get the estimation close to the 'Ignoring all COCOMO adjustment factors' case.* 

---

### 3. How was your experience? (Self-Assessment)
The AI tool acted as an effective interactive thought partner and execution assistant. It helped quickly explore the raw `effort_dataset.xlsx` dataset, surface the deterministic 1-to-1 relationship between `Urgency` and `Team Experience`, and verify the mathematical consistency between raw empirical productivity ($\sim 29.83 \text{ AdjFP/PM}$) and unadjusted base productivity ($\sim 34.15 \text{ AdjFP/PM}$). 

Working step-by-step through each section prevented cognitive overload and ensured each formula, Markdown explanation, and Python plot was mathematically validated prior to inclusion.

---

### 4. How would you rate your experience?
* **Qualitative Assessment:** **Excellent (5/5)**
* **Justification:** The AI provided instant code execution to inspect data distributions, generated clean Seaborn/Matplotlib visualizations, and successfully articulated complex risk management concepts (upper/lower bounds) in clear, professional language suitable for an academic submission.

---

### 5. What learning techniques did you gain from this?
* **COCOMO Decomposition:** Learned how to decouple raw project effort into "Base Effort" by dividing out the product of COCOMO cost drivers ($\text{EAF}$), allowing for scenario-based sensitivity analysis.
* **Dataset Pattern Recognition:** Realized the importance of cross-tabulating categorical features (such as `Urgency` vs. `Team Experience`) before making manual assumptions.
* **Calibrated Prompt Engineering:** Gained practical experience in prompting zero-shot LLMs by constraining productivity parameters ($\sim 30 \text{ AdjFP/PM}$) and explicitly instructing the model to ignore multipliers to mirror dataset-driven analogy results.

---

### 6. What is still missing?
* **Real-World COCOMO Refinement:** The preliminary estimate relies on synthetic boundary extremes (e.g., assuming *all* 15 factors are simultaneously Very Low or Extra High). In practice, projects feature a mix of high and low ratings across drivers.
* **Non-Linear Scaling:** Function point productivity often exhibits non-linear economies or diseconomies of scale as project size increases beyond $100 \text{ AdjFP}$, which simple linear analogy models do not fully capture.
* **Specific Stakeholder Input:** Once the Business Analyst receives feedback from the technical architect, exact ratings for critical factors like `CPLX` (Complexity) and `ACAP` (Analyst Capability) should replace the theoretical scenario bounds.
