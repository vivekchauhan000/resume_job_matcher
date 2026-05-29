# resume_job_matcher
🎯 An AI-powered resume &amp; job description matcher — uses NLP and semantic similarity to score compatibility, identify skill gaps, and provide actionable recommendations for job seekers and recruiters.
# 📄 Resume Job Matcher

<div align="center">

![Banner](https://img.shields.io/badge/Resume-Job_Matcher-6366f1?style=for-the-badge&logo=target&logoColor=white)

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![AI Powered](https://img.shields.io/badge/AI-Powered-ff6b35?style=for-the-badge&logo=openai&logoColor=white)]()
[![NLP](https://img.shields.io/badge/NLP-Enabled-8b5cf6?style=for-the-badge&logo=buffer&logoColor=white)]()
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)]()

---

### 🎯 Intelligently match resumes to job descriptions using AI & NLP — helping candidates land their dream jobs and recruiters find the perfect fit

[📋 Overview](#-overview) • [✨ Features](#-features) • [🏗️ Architecture](#%EF%B8%8F-architecture) • [🚀 Getting Started](#-getting-started) • [📁 Project Structure](#-project-structure) • [🤝 Connect](#-connect-with-me)

</div>

---

## 📋 Overview

**Resume Job Matcher** is an AI-powered tool that intelligently compares resumes against job descriptions to produce a compatibility score, skill gap analysis, and actionable recommendations — all in seconds.

Whether you're a **job seeker** wanting to tailor your resume, a **recruiter** screening hundreds of applications, or a **developer** building HR-tech solutions, this tool gives you an intelligent, unbiased analysis powered by state-of-the-art NLP models.

> 💡 *Stop guessing. Start matching. Land the job.*

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎯 **Smart Matching Score** | Calculates a compatibility percentage between resume & JD |
| 🧠 **Skill Extraction** | Automatically extracts hard & soft skills from both documents |
| 🔍 **Gap Analysis** | Highlights missing skills the candidate should acquire |
| 📊 **Detailed Report** | Generates a structured match report with recommendations |
| 📄 **Multi-Format Support** | Accepts PDF, DOCX, and plain text resumes |
| ⚡ **Bulk Screening** | Process multiple resumes against a single job description |
| 🌐 **REST API** | Integrate into any HR platform via clean API endpoints |
| 💾 **History Tracking** | Saves past matches for comparison and improvement |

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                        INPUT LAYER                           │
│          Resume (PDF/DOCX/Text)  +  Job Description          │
└──────────────────────┬───────────────────────────────────────┘
                       │
          ┌────────────┼────────────┐
          ▼                         ▼
  ┌───────────────┐        ┌────────────────┐
  │   RESUME      │        │   JOB DESC     │
  │   PARSER      │        │   PARSER       │
  │  (NLP + LLM)  │        │  (NLP + LLM)   │
  └──────┬────────┘        └───────┬────────┘
         │                         │
         ▼                         ▼
  ┌───────────────┐        ┌────────────────┐
  │  Skill &      │        │  Requirements  │
  │  Experience   │        │  & Keywords    │
  │  Extractor    │        │  Extractor     │
  └──────┬────────┘        └───────┬────────┘
         └──────────┬──────────────┘
                    ▼
         ┌─────────────────────┐
         │   MATCHING ENGINE   │
         │  (Semantic + TF-IDF │
         │   + Cosine Sim)     │
         └──────────┬──────────┘
                    │
         ┌──────────┼──────────┐
         ▼          ▼          ▼
  ┌──────────┐ ┌─────────┐ ┌──────────────┐
  │  Match   │ │  Gap    │ │  Recommend-  │
  │  Score   │ │ Report  │ │  ations      │
  └──────────┘ └─────────┘ └──────────────┘
                    │
                    ▼
         ┌─────────────────────┐
         │   OUTPUT / API      │
         │   JSON + PDF Report │
         └─────────────────────┘
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10+
- pip / conda
- API keys (OpenAI / Anthropic / HuggingFace)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/vivekchauhan000/resume_job_matcher.git

# 2. Navigate into the project
cd resume_job_matcher

# 3. Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 4. Install dependencies
pip install -r requirements.txt

# 5. Set up environment variables
cp .env.example .env
# Edit .env with your API keys
```

### Running the Matcher

```bash
# Match a single resume to a job description
python main.py --resume path/to/resume.pdf --job path/to/jd.txt

# Bulk match multiple resumes
python main.py --bulk --resumes_dir ./resumes/ --job path/to/jd.txt

# Start the API server
uvicorn api.server:app --reload --port 8000
```

### Sample Output

```json
{
  "match_score": 87.4,
  "matched_skills": ["Python", "Machine Learning", "FastAPI", "SQL"],
  "missing_skills": ["Docker", "Kubernetes", "CI/CD"],
  "experience_match": "Strong",
  "recommendation": "Great fit! Consider adding Docker & cloud deployment skills.",
  "report_path": "./reports/match_report_2024.pdf"
}
```

---

## 📁 Project Structure

```
resume_job_matcher/
│
├── 📂 parsers/
│   ├── resume_parser.py         # Extracts info from resumes (PDF/DOCX/Text)
│   └── jd_parser.py             # Parses job description requirements
│
├── 📂 extractors/
│   ├── skill_extractor.py       # NLP-based skill & keyword extractor
│   └── experience_extractor.py  # Work experience parser
│
├── 📂 matcher/
│   ├── scoring_engine.py        # Cosine similarity + semantic matching
│   ├── gap_analyzer.py          # Identifies missing skills/requirements
│   └── recommender.py           # Generates improvement recommendations
│
├── 📂 api/
│   ├── server.py                # FastAPI server
│   └── routes.py                # API route definitions
│
├── 📂 reports/
│   └── report_generator.py      # PDF report builder
│
├── 📂 models/
│   └── schemas.py               # Pydantic data models
│
├── 📂 utils/
│   ├── file_handler.py          # File reading utilities
│   └── config.py                # Config loader
│
├── 📂 tests/
│   └── test_matcher.py          # Unit & integration tests
│
├── .env.example                 # Environment variable template
├── requirements.txt             # Python dependencies
├── main.py                      # CLI entry point
└── README.md                    # You are here!
```

---

## 🛠️ Tech Stack

<div align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=chainlink&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![spaCy](https://img.shields.io/badge/spaCy-09A3D5?style=flat-square&logo=spacy&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=flat-square&logo=postgresql&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)

</div>

---

## 🤝 Connect with Me

<div align="center">

I'm always open to collaborating on exciting AI/ML projects!

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Vivek_Chaudhary-0a66c2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/vivek-chaudhary-438a5524a)
[![GitHub](https://img.shields.io/badge/GitHub-vivekchauhan000-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/vivekchauhan000)

</div>

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with ❤️ by [Vivek Chaudhary](https://github.com/vivekchauhan000)

⭐ *If you found this useful, please consider giving it a star!* ⭐

</div>
