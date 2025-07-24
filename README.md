# 📖 GitaGraph: Unveiling Connections in the Bhagavad Gita with NLP and Graph Neural Networks

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![License](https://img.shields.io/badge/License-MIT-lightgrey)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

> 📘 Final Semester MCA Project | National Institute of Technology Jamshedpur  
> 👨‍🎓 Submitted by: **Arekanti Hanook** (2022PGCSCA093)  
> 🧑‍🏫 Supervised by: **Dr. Amit Majumder**, Dept. of Computer Science & Engineering

---

## 📚 Dataset

- 📖 **Source**: English-translated verses from the Bhagavad Gita (Chapters 1–3)
- 👤 **Entities**: ~120 characters (Arjuna, Krishna, Bhima, Kunti, Draupadi, etc.)
- 🔗 **Relationships**: ~784 annotated edges
- 🔁 **Relation types**: father, mother, brother, cousin, husband, teacher, friend
- 📊 **Splits**:
  - Train: 550
  - Dev: 117
  - Test: 117

---

## 🧱 Architecture

### 1. NLP Pipeline
- `spaCy` used for Named Entity Recognition (NER) tagging (`B-PER` / `I-PER`)
- Epithets handled (e.g., `"Partha"` → `"Arjuna"`)
- Rule-based relationship extraction  
  _Example: “Arjuna is son of Kunti” → `Arjuna-son-Kunti`_

### 2. Graph Construction
- Nodes: Characters
- Edges: Directed, labeled relationships
- Validation with gender and Mahabharata domain rules

### 3. R-GCN (Relational Graph Convolutional Network)
- Built using **PyTorch Geometric**
- Node features: mention count, gender, in/out-degree, clustering coefficient
- Edge prediction via relation-specific message passing
- ✅ Accuracy: `85%` | Macro F1 Score: `0.80`

### 4. Interactive Prediction

```python
predict_relationship("Krishna", "Bhima")  
# Output: "cousin" (confidence: 85%)
