# 🧠 Automated Misinformation Detection Pipeline Using KNIME

This project demonstrates an end-to-end misinformation detection pipeline using **KNIME Analytics Platform**, integrated with **Python** and **transformer-based AI models**. It collects news data in real-time, classifies it as real or fake, visualizes trends, and automates reporting.

---

## 📌 Problem Statement

The unchecked spread of fake news has become a major threat in today’s digital world. Manual fact-checking can't keep pace with the scale of misinformation. This project aims to create a **real-time, automated solution** to detect, classify, and track misinformation using AI.

---

## 💡 Proposed Solution

Using **KNIME** and **Python**, the system performs:

- ✅ Real-time data collection from NewsAPI  
- ✅ NLP-based text preprocessing  
- ✅ Fake news classification using a RoBERTa transformer model  
- ✅ Visualization of misinformation trends  
- ✅ Automated daily reporting via email  

---

## 🔧 Tools & Technologies

- **KNIME Analytics Platform**
- **Python 3** (via Anaconda/Miniconda)
- **Libraries**: `pandas`, `transformers`, `torch`, `plotly`, `seaborn`
- **KNIME Nodes**: `GET Request`, `JSON Path`, `Python Script`, `Bar Plot`, `Pie Chart`, `Send Email`, etc.
- **Model**: Pre-trained **RoBERTa** (for fake/real classification)

---

## 🧭 Workflow Overview

### 1. **Data Collection**
- API: [NewsAPI](https://newsapi.org/)
- Retrieves articles mentioning the keyword: `misinformation`
- KNIME Nodes:
  - `GET Request` → fetches news JSON
  - `JSON Path` & `Ungroup` → extract fields (title, content, etc.)
  - `Excel Writer` → save structured data

### 2. **Text Preprocessing**
- KNIME `Python Script Node`:
  - Lowercasing
  - Remove punctuation & special characters
  - Remove stopwords
  - Clean extra whitespaces

### 3. **Fake News Classification**
- RoBERTa model loaded via Python
- Tokenization and softmax activation for class probability
- Class `0`: Fake News  
- Class `1`: Real News  
- Output saved to Excel

### 4. **Visualization of Trends**
- Bar Plot → Top misinformation sources  
- Pie Chart → Distribution of fake vs. real  
- Area Chart → Fake news spread over time  
- KNIME Nodes: `GroupBy`, `Bar Plot`, `Stacked Area Chart`, `Table View`

### 5. **Automated Reporting**
- `Send Email Node` sends a report after pipeline execution
- Attachments include daily Excel/CSV summary
- SMTP Configurable (e.g., Gmail: smtp.gmail.com, port 587)

---

## ⚙️ Setup Instructions

### 1. Install KNIME
Download and install from: https://www.knime.com/downloads

### 2. Install Required KNIME Extensions
Navigate to `File → Install KNIME Extensions`, then search and install:
- KNIME Python Integration
- KNIME Text Processing
- KNIME Deep Learning – TensorFlow 2 Integration

### 3. Configure Python in KNIME
Recommended via Anaconda:

```bash
conda create -n knime_env python=3.8
conda activate knime_env
pip install pandas transformers torch plotly seaborn

Then in KNIME:
Go to Preferences → KNIME → Python and link to knime_env.

📤 Output & Reports
.✅ Cleaned dataset (Excel format)
.✅ Predictions of Real/Fake labels
.✅ Visual dashboards inside KNIME (bar, pie, area charts)
.✅ Automatically emailed daily reports to stakeholders

🚧 Challenges Faced
| Issue                               | Solution                                                  |
| ----------------------------------- | --------------------------------------------------------- |
| KNIME extension installation errors | Manual installation and preference tuning                 |
| Python integration failures         | Created separate conda environment with specific packages |
| Lost progress due to KNIME crash    | Adopted frequent manual saves and backup strategy         |
| Disappearing extensions             | Reinstallation and KNIME directory reconfiguration        |
| Email node SMTP failures            | Fixed port/auth settings and validated credentials        |

📈 Future Improvements

.Integrate Apache Airflow for full workflow automation
.Support multiple data sources (Reddit, Twitter)
.Deploy as a web app/dashboard
.Add multilingual misinformation detection

👨‍💻 Developed By
Abdul Zuhail M
🧪 Data Intelligence Research Lab – Quantum Wolf
📅 Project Duration: 08-02-2025 to 12-02-2025

📃 License
This project is intended for academic and educational use only. Please refer to NewsAPI's Terms of Use before using in production.

---



