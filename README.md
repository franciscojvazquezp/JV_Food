# 🍽️ JV Food — A/A/B Test & Funnel Analysis
 
<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-Data%20Wrangling-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/SciPy-Z--Test-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white"/>
  <img src="https://img.shields.io/badge/StatsModels-Holm--Bonferroni-4B8BBE?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Matplotlib%20%7C%20Seaborn-Visualization-11557C?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Status-Complete-1D9E75?style=for-the-badge"/>
</p>
<p align="center">
  <i>A font change was tested on 7,500+ users across a 5-stage funnel.<br>
  The experiment found no winner — but the data revealed exactly where the real problem is.</i>
</p>
 
## 🔥 Overview
 
A food delivery app ran an **A/A/B experiment** to evaluate whether a font redesign (Group 248) improved conversion across the purchase funnel. Two identical control groups (246 & 247) validated the experiment baseline before any treatment comparison.
 
**The core question:** Did the font change move the needle?  
**The real discovery:** The problem was never the font.
 
---
 
## 🔍 What's Inside the Notebook
 
### 1. 🧹 Data Cleaning & EDA
- Duplicate detection and removal
- Date filtering — records before Aug 1st dropped (only 0.99% of data, but incomplete)
- Power user analysis: P25=9 · P50=20 · P75=37 · **P99=200 events** — large gap signals a highly engaged segment
- Funnel reconstruction from raw event logs
### 2. 📊 Funnel Analysis
Full conversion breakdown across all 5 stages. Identifies the critical drop-off point and separates it from healthy conversion steps.
 
### 3. 🧪 A/A Validation
Before any treatment comparison, Groups 246 & 247 are tested against each other.  
**Why it matters:** If two identical groups differ statistically, the experiment is broken. They didn't — baseline confirmed ✅
 
### 4. ⚡ A/B Statistical Testing
- **Z-test for proportions** — conversion rate comparison at each funnel stage
- **12 total comparisons** — 4 stages × 3 group pairings (246/247 · 246/248 · 247/248 · Combined/248)
- **Holm-Bonferroni correction** — controls Type I error (false positives) across all 12 tests
---
 
## 📈 Key Results
 
### The Funnel
 
```
┌──────────────────┐
│   Main Screen    │  100.0%  →  7,534 users
└────────┬─────────┘
         │  ⚠️  -38.1% DROP  ← THE REAL PROBLEM
┌────────▼─────────┐
│  Offers Screen   │   61.9%  →  4,663 users
└────────┬─────────┘
         │  -11.6%
┌────────▼─────────┐
│   Cart Screen    │   50.3%  →  3,790 users
└────────┬─────────┘
         │  -2.6%
┌────────▼─────────┐
│     Payment      │   47.7%  →  3,594 users
└──────────────────┘
```
 
> **🚨 Biggest drop:** Main Screen → Offers = **38.1% of all users lost**  
> **✅ Good news:** Once past Offers → Cart: **81.3%** · Cart → Payment: **94.8%**  
> The product sells itself. Users just never get to see it.
 
---
 
### The A/B Test — All 12 Results
 
| Comparison | Stage | Raw p-value | Corrected p | H₀ Rejected? |
|:---|:---|:---:|:---:|:---:|
| 246 vs 247 | Offers | 0.262 | 1.0 | ❌ No |
| 246 vs 247 | Cart | 0.240 | 1.0 | ❌ No |
| 246 vs 247 | Payment | 0.120 | 1.0 | ❌ No |
| 246 vs 248 | Offers | 0.268 | 1.0 | ❌ No |
| 246 vs 248 | Cart | 0.101 | 1.0 | ❌ No |
| 246 vs 248 | Payment | 0.258 | 1.0 | ❌ No |
| 247 vs 248 | Offers | 0.987 | 1.0 | ❌ No |
| 247 vs 248 | Cart | 0.641 | 1.0 | ❌ No |
| 247 vs 248 | Payment | 0.670 | 1.0 | ❌ No |
| Control vs 248 | Offers | 0.531 | 1.0 | ❌ No |
| Control vs 248 | Cart | 0.224 | 1.0 | ❌ No |
| Control vs 248 | Payment | 0.686 | 1.0 | ❌ No |
 
**All 12 corrected p-values = 1.0 → the font change had zero measurable impact at any stage.**
 
---
 
## 💡 Conclusions & Recommendations
 
The A/B test is conclusive: the font redesign did not affect user behavior.  
But the funnel analysis tells a different story — and points directly to the next move.
 
| Priority | Recommendation |
|:---:|:---|
| 🔴 **High** | Redesign the Main Screen CTA — drive users to explore Offers before they bounce |
| 🟡 **Medium** | A/B test personalized offer banners based on user history |
| 🟢 **Future** | Triggered push notifications for users who landed on Main Screen with no Offer click |
 
> Don't optimize the checkout. Fix the first click.
 
---
 
## 🛠️ Tech Stack
 
<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white"/>
  <img src="https://img.shields.io/badge/SciPy-8CAAE6?style=flat-square&logo=scipy&logoColor=white"/>
  <img src="https://img.shields.io/badge/StatsModels-4B8BBE?style=flat-square"/>
  <img src="https://img.shields.io/badge/Matplotlib-11557C?style=flat-square"/>
  <img src="https://img.shields.io/badge/Seaborn-4C9BE8?style=flat-square"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white"/>
</p>
---
 
## ⚙️ Setup
 
Clone the repo:
```bash
git clone https://github.com/franciscojvazquez/JV_Food.git
cd JV_Food
```
 
Install dependencies:
```bash
pip install -r requirements.txt
```
 
Launch the notebook:
```bash
jupyter notebook JV-Food.ipynb
```
 
---
 
## 📁 Project Structure
 
```
JV_Food/
├── JV-Food.ipynb           # Full analysis notebook
├── JV_Food_Insights.pdf    # Executive report — key visuals & insights
├── logs_exp_us.csv         # Raw event dataset
├── requirements.txt        # Python dependencies
└── README.md
```
 
---
 
<p align="center">
  Made by <strong>Francisco Javier Vázquez Patiño</strong><br>
  Industrial Engineer → Data Analyst<br>
  13+ years in automotive manufacturing · TripleTen Bootcamp Sprint 12<br><br>
  <a href="https://www.linkedin.com/in/franciscojaviervazquezpatino">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
  </a>
  &nbsp;
  <a href="https://github.com/franciscojvazquez">
    <img src="https://img.shields.io/badge/GitHub-Portfolio-181717?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
</p>
