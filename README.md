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
```

## ⚙️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your_username/GitaGraph.git
cd GitaGraph
```
### 2. Create a Virtual Environment (optional)
```python
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```
### 3. Install Dependencies
```python
pip install -r requirements.txt
```
### 4. Run the Jupyter Notebook
```python
jupyter notebook BhagwadGita.ipynb
```


---

### 📊 2. **Visualization Section (if you use pyvis/networkx)**

```markdown
## 📊 Visualization

- Interactive graphs created using **pyvis** and **networkx**
- Highlights:
  - Arjuna ➝ Husband ➝ Draupadi
  - Krishna ➝ Cousin ➝ Bhima
  - Kunti ➝ Mother ➝ Arjuna
- Graphs saved as `.html` for easy visualization

```
## 🔮 Future Work

- Expand to all 18 chapters
- Add attention-based GNNs
- Build a web app using Streamlit or Flask
- Integrate with full Mahabharata character graph

## 🙏 Acknowledgements

- Bhagavad Gita open-source translations
- Dr. Amit Majumder (NIT Jamshedpur)
- Libraries used: spaCy, PyTorch Geometric, PyVis, NetworkX
## 📬 Contact

**Arekanti Hanook**  
MCA (2022–2025), NIT Jamshedpur  
📧 Email: arekantihanook123@gmail.com 
🌐 GitHub: [@hanookarekanti](https://github.com/hanookarekanti)

