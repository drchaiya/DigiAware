# DigiAware
It is a complex text validation in LLM for high stake domains.

# 🧠 DigiAware: A Meta-Cognitive Framework for Generative AI Calibration

## 💡 Overview: The Semantic Power Factor ($\mathbf{SPF}$) and Power Analogy

The **DigiAware** framework addresses the critical issue of **hallucination** in Large Language Models (LLMs) by reframing it as an intrinsic component of fluency, which we call **Reactive Generative Output ($\mathbf{RGO}$ or $\mathbf{Q}$)**.

We draw an analogy from the electrical **Power Triangle**:

1.  **Active Confidence ($\mathbf{P}$ or $\mathbf{U_{o}^{\text{meta}}}$):** The **verifiable truth** component (useful work).
2.  **Reactive Generative Output ($\mathbf{RGO}$ or $\mathbf{Q}$):** The **non-factual component** (hallucination) necessary for fluent, human-like generation—the **Stochastic Persona**.
3.  **Apparent Confidence ($\mathbf{S}$):** The **total output confidence** magnitude, where $\mathbf{S}^2 = \mathbf{P}^2 + \mathbf{Q}^2$.

The goal of DigiAware is to maximize the **Semantic Power Factor ($\mathbf{SPF} = \mathbf{P/S}$)**, which measures the factual purity of the output. **$\mathbf{SPF}$ is mandated by external verification ($\mathbf{T_c}$)**.



---

## 🛠️ Framework Mechanism: $\mathbf{T_c}$ as the $\mathbf{RGO}$ Suppressor

DigiAware compels the model to calculate a self-awareness score, the **Active Confidence ($\mathbf{P}$)**, using three components:

### 1. Input Fidelity ($\mathbf{U_i}$)
Measures the quality of the input and the model's ability to access context, including penalties for architectural risks:

* **Lost in the Middle (LiTM) Decay:** Penalizes key facts buried deep in the context.
* **Contextual State Decay (Fatigue):** Penalizes state degradation in multi-turn conversations ($T^2$ relationship).
* **Prompt Ambiguity Score (PAS):** Penalizes unclear user input.

$$\mathbf{U_i} = \mathbf{RCS}_{\text{base}} \cdot \mathbf{Decay}_{\text{LiTM}} \cdot \mathbf{Decay}_{\text{Fatigue}} \cdot \mathbf{Decay}_{\text{PAS}}$$

### 2. Output Confidence ($\mathbf{U_o}$)
The model's internal fluency and certainty in its token sequence, irrespective of factual correctness.
$$\mathbf{S} = \mathbf{U_i} \cdot \mathbf{U_o}$$

### 3. Trustworthiness Validation ($\mathbf{T_c}$) - The Critical Suppressor
This is a **mandatory external filter** against verified, domain-specific knowledge bases ($\mathbf{K}$). It is the core mechanism that **enforces the $\mathbf{SPF}$**.

* **Design Constraint:** By construction, the $\mathbf{T_c}$ score **mandates** the final $\mathbf{SPF}$: $$\mathbf{SPF} \equiv \frac{\mathbf{T_c}}{100}$$
* **Absolute Suppression:** If a high-risk entity is confirmed as a **Known Fabrication** (e.g., non-existent legal case), $\mathbf{T_c}$ is immediately set to $\mathbf{0\%}$. This forces **Active Confidence ($\mathbf{P}$) to zero**, guaranteeing $\mathbf{SPF}=0$.
* **Severe Penalty (Contextual Contradiction):** Penalty is calculated based on semantic divergence ($\mathbf{D_s}$) from $\mathbf{K}$.

### Final Active Confidence ($\mathbf{P}$)

The final score ($\mathbf{P}$) is calculated by applying the external penalty to the total Apparent Confidence ($\mathbf{S}$):

$$\mathbf{P} = \mathbf{U_{o}^{\text{meta}}} = \underbrace{(\mathbf{U_i}) \cdot (\mathbf{U_o})}_{\mathbf{S}} \cdot \left(\frac{\mathbf{T_c}}{100}\right)$$

---

## 🛑 Action Protocol: Active Abstention

The final $\mathbf{P}$ score maps to a four-level, color-coded scale that enforces the **Active Abstention** policy. This is designed for **targeted high-stakes domains** (e.g., Legal, Healthcare).

| Level | Color | Range ($\mathbf{P}$) | Action / Interpretation |
| :---: | :---: | :------------------: | :---------------------- |
| 1 | Green | $\ge 95\%$ | High Confidence. Deliver final answer. |
| 2 | Yellow | $85\% \le \mathbf{P} < 95\%$ | Standard Confidence. Deliver answer with minor caveat. |
| 3 | Orange | $75\% \le \mathbf{P} < 85\%$ | Cautionary Confidence. Strong warning, prompting human review. |
| 4 | **Red** | **$< 75\%$** | **Low Confidence/High Risk. Immediate Escalation/Abstention. Model must yield control.** |

> **Failsafe Ceiling:** If the $\mathbf{T_c}$ check exceeds the maximum allowed time (Latency Budget), the output is capped at the Level 3/Orange threshold ($\mathbf{P} \le 75\%$). This ensures **no unverified output can be classified as high confidence.**

---

## 🔑 Key Terminology

| Term | Conceptual Definition |
| :--- | :--- |
| **Reactive Generative Output ($\mathbf{Q}$)** | The non-factual component (hallucination) calculated as the **residual magnitude** $\mathbf{Q} = \sqrt{\mathbf{S}^2 - \mathbf{P}^2}$. |
| **Semantic Power Factor ($\mathbf{SPF}$)** | The purity ratio $\mathbf{P/S}$, **mandated** to equal $\mathbf{T_c}/100$. |
| **Active Confidence ($\mathbf{P}$)** | The verifiable, factually correct output component. |
| **Trustworthiness Validation ($\mathbf{T_c}$)** | The mandatory external check acting as the critical $\mathbf{RGO}$ suppressor. |
| **Absolute Suppression** | The policy of setting $\mathbf{T_c}=0\%$ when a high-risk entity is a **Known Fabrication**. |
