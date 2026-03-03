# SCOREval - Multi-dimensional Assessment and Explainable Feedback for Counselor Responses to Client Resistance

This repository contains the code, data, and models for the paper:

> **"Multi-dimensional Assessment and Explainable Feedback for Counselor Responses to Client Resistance in Text-based Counseling with LLMs"**  

We propose a theory-driven framework and a fine-tuned LLM (Llama-3.1-8B) to evaluate counselor responses to client resistance across four communication mechanisms. The model provides multi-dimensional ratings and natural language explanations, and has been shown to improve counselor performance in a controlled experiment.

---

## 📌 Overview

<div align="center">
<img src="figures/figure.png" alt="Example" width="400"/>
</div>

Counselor responses to client resistance are critical yet challenging to evaluate at scale. We introduce:

- A **four-dimensional framework** for evaluating counselor responses:
  - Respect for Autonomy
  - Stance Alignment
  - Emotional Resonance
  - Conversational Orientation

- A **high-quality annotated dataset** of 3,836 real-world counseling excerpts with expert ratings and explanations.

- A **fine-tuned Llama-3.1-8B model** that:
  - Classifies response quality across three levels (No / Weak / Strong expression)
  - Generates free-text explanations grounded in the framework

- A **proof-of-concept study** showing that AI-generated feedback improves counselors' ability to respond to client resistance.

---

## 🧠 Framework

Each counselor response is evaluated along four dimensions (Respect for Autonomy,  Emotional Resonance, Stance Alignment, Conversational Orientation), each with three levels (No Expression | Weak Expression | Strong Expression).

---

## 📊 Dataset

- **Source**: Two publicly available Chinese counseling dialogue datasets (ClientBehavior, ObserverWAI)
- **Resistance detection**: Using RECAP (91.41% accuracy)
- **Annotation**: 5 licensed counselors with >10 years experience
- **Inter-annotator agreement**: Cohen’s κ = 0.74–0.77
- **Explanations**: Rated highly (2.8–2.9/3.0) on consistency, anchoring, and clarity

The dataset will be released for research purposes under a data-sharing agreement.

---

## 🚀 Model

We fine-tune **Llama-3.1-8B-Instruct** on our dataset with full-parameter tuning.

- **Input**: Dialogue history + counselor response
- **Output**: 
  - 4 dimension-level labels (0/1/2)
  - Free-text explanation

### Performance Highlights

| Metric | Our Model | Best Baseline (GPT-4o / Claude) |
|--------|-----------|----------------------------------|
| Macro F1 (Respect for Autonomy) | **80.9** | 45.4 |
| Macro F1 (Stance Alignment) | **77.6** | 58.6 |
| BLEU-1 (Explanation) | **60.3** | 32.5 |
| Human Ratings (1–3) | **2.8–2.9** | 1.9–2.4 |

---

## 🧪 Experiment with Counselors

We conducted a **mixed between-within experiment** with 43 novice counselors:

- **Experimental group** received AI-generated feedback on their responses
- **Control group** received no feedback
- **Result**: Significant improvement across all four dimensions for the experimental group (p < .01)

Participants also rated the system highly for:
- Awareness of improvement areas (4.38/5)
- Clarity of feedback (4.14/5)
- Confidence in managing resistance (3.86/5)

---


## 🔧 Requirements

- Python 3.9+
- PyTorch 2.0+
- Transformers 4.40+
- Llama-3.1-8B-Instruct

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## ⚠️ Ethics Statement

- All data is de-identified and released under strict research agreements.
- The model is **not** intended to replace clinical judgment.
- This work was approved by the Institutional Review Board of the authors' institution.

---

## 🙏 Acknowledgments

We thank the annotators and counselors who participated in this study, and the developers of the source datasets.

