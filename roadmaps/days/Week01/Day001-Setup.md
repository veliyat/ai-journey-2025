# Day 001 — Environment Setup & Repo Initialization  

---

## 🕐 Tier 1 (1h) — Core  

- Install **Python 3.11** and **VS Code** 
- Go to your desired project folder (eg. cd ~/Documents/projects/ai-journey-2025)
- Create & activate a **virtual environment**:  

```bash
# Create a directory and navigate to that directory
mkdir ~/Documents/projects/ai-journey-2025 
cd ~/Documents/projects/ai-journey-2025

# Create venv (for some installations "python3" might work instead of "python")
python -m venv .venv  

# Activate (Linux/macOS)
source .venv/bin/activate  

# Activate (Windows)
#.venv\Scripts\activate
```  

- Install dependencies:  

```bash
pip install numpy pandas matplotlib scikit-learn jupyter
pip freeze > requirements.txt
```  

- Create a GitHub repo **ai-journey-2025** (No README to be added at the start)
- Initialize a git repo on local machine and add that to our GitHub repo:  

```bash
git init
git add .
git commit -m "Initial commit - project setup"
#Replace "yourusername" with your GitHub username
git remote add origin https://github.com/yourusername/my-ai-journey.git
git branch -M main
git push -u origin main
```  

---

## ⏱️ Tier 2 (2h) — Extend  

- Create folder structure:  

```bash
mkdir roadmaps notebooks projects logs assets
```  

- Create & test first notebook:  

```python
# Inside notebooks/week1_basics.ipynb
import numpy as np
import pandas as pd

arr = np.array([1, 2, 3])
print("Numpy array:", arr)

df = pd.DataFrame({"col1": [1, 2], "col2": [3, 4]})
print("Pandas DataFrame:\n", df)
```

---

## ⏳ Tier 3 (3h) — Advance  

- Add reflection log: `logs/week1_reflections.md`  

```markdown
# Week 1 — Reflections
## Day 001
- What I did:
- What I learned:
- Challenges:
- Next steps:
```  

- Save a **screenshot** of your first notebook output to `assets/`.  

---

## 🔥 Tier 4 (4h) — Polish  

- Create a tiny pytest test in `tests/test_sanity.py`:  

```python
def test_sum():
    assert sum([1, 2, 3]) == 6
```  

- Add GitHub Actions workflow: `.github/workflows/python-app.yml`  

```yaml
name: Python package

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: "3.11"
      - name: Install dependencies
        run: pip install -r requirements.txt
      - name: Run tests
        run: pytest
```  

---

## ✅ Deliverable  
- **Repo pushed** with structure, working notebook, and (optionally) CI/CD set up  

---

## 📚 Choose Your Adventure (Optional References)  
- Book: [*Python Crash Course* (Eric Matthes)](https://nostarch.com/pythoncrashcourse2e) — setup & environments  
- Video: [FreeCodeCamp — Python for Beginners (4h)](https://www.youtube.com/watch?v=rfscVS0vtbw)  
- Blog: [Real Python — Virtual Environments Primer](https://realpython.com/python-virtual-environments-a-primer/)  

---

🔗 *Navigation:* [⬅️ Back to Week 01 Overview](./README.md) | [🌍 RoadMapUltimate](../../RoadMapUltimate.md)  
