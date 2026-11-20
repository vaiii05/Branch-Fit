<div align="center">

# 🧭 BranchFit

### *Answer less. Learn more. Find the engineering branch that fits you.*

An adaptive, ML-powered questionnaire that recommends the right engineering branch, choosing each next question based on your previous answers.

<br>

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Render](https://img.shields.io/badge/Deployed_on-Render-46E3B7?style=for-the-badge&logo=render&logoColor=white)

[🚀 **Live Demo**](https://branchfit1.onrender.com/) · [📖 Setup Guide](SETUP_INSTRUCTIONS.md) · [🐛 Report Bug](https://github.com/vaiii05/Branch-Fit/issues) · [💼 LinkedIn](https://www.linkedin.com/in/vaibhavi-rai-2b6110357/)

</div>

---

## 📌 Overview

Choosing an engineering branch is hard, and long generic quizzes don't help much. **BranchFit** asks fewer, smarter questions. After every answer, a trained Random Forest model updates its belief about which branch suits you, and the system picks the *most informative* next question. The test ends as soon as the model is confident.

---

## ✨ Highlights

| | Feature | Description |
|---|---|---|
| 🧠 | **Adaptive Questioning** | Every answer reshapes the next question using information gain and uncertainty sampling |
| 🎯 | **Two Test Modes** | A general test across all branches, or a focused suitability test for one branch |
| ⚡ | **Early Stopping** | Ends once the model reaches 80% confidence, with no filler questions |
| 🔁 | **No Repetition** | Questions are never asked twice in a session |
| 📄 | **PDF Reports** | Download your results and top recommendations |
| 📊 | **History & Admin Analytics** | Track past tests, with an admin dashboard for aggregate insights |
| 🔐 | **Secure Accounts** | Registration, login and hashed passwords backed by MongoDB Atlas |

---

## 🧬 How It Works

```mermaid
flowchart LR
    A[10 Screening<br>Questions] --> B[Random Forest<br>Predicts Branch Probabilities]
    B --> C{Confidence<br>≥ 80%?}
    C -- No --> D[Select Most Informative<br>Next Question]
    D --> B
    C -- Yes --> E[🎓 Final Recommendation<br>+ PDF Report]
```

1. **Screen**: the user answers 10 initial Likert-scale questions (1–5).
2. **Predict**: unanswered questions default to neutral, and the Random Forest returns a probability for each of 5 branches.
3. **Adapt**: `TrueAdaptiveSystem` ranks the remaining pool of 30 adaptive questions by expected information gain.
4. **Conclude**: after at least 10 answers, the test stops once confidence reaches 80%, or when it hits the question cap (30 for the general test).

### 🎓 Branches Covered

| Branch | Focus Areas |
|---|---|
| 💻 **Computer Engineering** | Hardware design, digital circuits, embedded systems, VLSI |
| 📡 **EXTC** | Signal processing, communication systems, RF, network protocols |
| ⚡ **Electrical** | Power systems, electrical machines, control systems, power electronics |
| 🖥️ **Information Technology / CSE** | Programming, databases, web development, data structures |
| ⚙️ **Mechanical** | Mechanical design, thermodynamics, manufacturing, CAD/CAM |

---

## 🤖 The Model

| | |
|---|---|
| **Algorithm** | Random Forest Classifier (100 trees) |
| **Preprocessing** | StandardScaler |
| **Dataset** | 1,000 balanced, augmented responses (200 per branch) |
| **Features** | 60 Likert-scale questions |
| **Accuracy** | ~87% |
| **Question selection** | Information gain + uncertainty sampling |

---

## 🛠️ Tech Stack

<table>
<tr><td><b>Backend</b></td><td>Python · Flask · Flask-Login · Flask-WTF</td></tr>
<tr><td><b>Machine Learning</b></td><td>scikit-learn · NumPy · pandas · joblib</td></tr>
<tr><td><b>Database</b></td><td>MongoDB Atlas (PyMongo)</td></tr>
<tr><td><b>Reports</b></td><td>ReportLab (PDF) · openpyxl</td></tr>
<tr><td><b>Frontend</b></td><td>Jinja2 templates · Bootstrap · Font Awesome</td></tr>
<tr><td><b>Deployment</b></td><td>Gunicorn · Render</td></tr>
</table>

---

## 🚀 Getting Started

**Prerequisites:** Python 3.10+ and a free [MongoDB Atlas](https://www.mongodb.com/atlas) cluster.

```bash
# 1. Clone the repository
git clone https://github.com/vaiii05/Branch-Fit.git
cd Branch-Fit/"branch fit"

# 2. Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure environment variables
cp .env.example .env            # Windows: copy .env.example .env

# 5. Run the app
python app.py                   # → http://localhost:5000
```

<details>
<summary><b>⚙️ Environment variables</b></summary>

```env
SECRET_KEY=your_secret_key
FLASK_ENV=development
MONGO_URI=your_mongodb_atlas_connection_string
ADMIN_USERNAME=your_admin_username
ADMIN_PASSWORD=your_admin_password
```

Your Atlas connection string looks like:
`mongodb+srv://USERNAME:PASSWORD@your-cluster.mongodb.net/branchfit?retryWrites=true&w=majority`

See [SETUP_INSTRUCTIONS.md](SETUP_INSTRUCTIONS.md) for step-by-step Atlas setup.
</details>

<details>
<summary><b>🔁 Retrain the model</b></summary>

```bash
python retrain_model.py
```

This trains a new Random Forest on `balanced_dataset_augmented.csv` and regenerates `model.pkl` and `scaler.pkl`.
</details>

<details>
<summary><b>☁️ Deploy on Render</b></summary>

1. Push the repo to GitHub
2. Create a new **Web Service** on Render and connect the repo
3. Set the root directory to `branch fit`
4. Build command: `pip install -r requirements.txt`
5. Start command: `gunicorn app:app`
6. Add the environment variables above in the Render dashboard
</details>

---

## 🔌 Main Routes

| Route | Purpose |
|---|---|
| `/register` · `/login` | Create an account and sign in |
| `/dashboard` | Choose a general or branch-specific test |
| `/general-test` | Start the all-branch adaptive test |
| `/branch-test/<branch>` | Start a branch suitability test |
| `/question` · `/submit-answer` | Serve a question and record the answer |
| `/results` | View branch probabilities and recommendations |
| `/download-result` | Download the PDF report |
| `/test-history` | Review past test attempts |
| `/admin/dashboard` | Admin analytics |

---

## 📁 Project Structure

```
Branch-Fit/
└── branch fit/
    ├── app.py                          # Flask routes: auth, tests, results, admin
    ├── adaptive_system_v2.py           # Adaptive question-selection engine
    ├── retrain_model.py                # Model training pipeline
    ├── auth.py · forms.py              # Authentication and form validation
    ├── balanced_dataset_augmented.csv  # Training dataset
    ├── branchfit_questions_final.xlsx  # Question → branch mapping
    ├── adaptive_questions.json         # Screening + adaptive question pool
    ├── branch_labels.json              # Class index → branch name
    ├── model.pkl · scaler.pkl          # Trained model and scaler
    ├── templates/                      # Jinja2 HTML templates
    └── static/                         # CSS
```

---

## 🗺️ Roadmap

- [ ] Persist in-progress test sessions in MongoDB
- [ ] Train on real student responses
- [ ] Explainability: show *why* a branch was recommended
- [ ] Add more branches (Civil, Chemical, Biomedical)

---

<div align="center">

**Built by [Vaibhavi Rai](https://github.com/vaiii05)**
B.Tech IT (AIML Hons.), Fr. CRIT, Vashi 🎓

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/vaibhavi-rai-2b6110357/)

⭐ Star this repo if it helped you pick a branch!

</div>
