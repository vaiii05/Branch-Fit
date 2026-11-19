<div align="center">

# 🎯 BranchFit: ML Engineering Branch Recommender

**Not sure which engineering branch to choose? Let data decide.**

[**🌐 Live Demo**](https://branchfit1.onrender.com)

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![Render](https://img.shields.io/badge/Deployed%20on-Render-46E3B7?style=for-the-badge&logo=render&logoColor=white)

</div>

---

## 📌 The Problem

Choosing an engineering branch is one of the biggest decisions a student makes, and it's often based on trends, peer pressure or guesswork.

**BranchFit** takes a student's academic profile, skills and interests and uses a trained **Random Forest classifier** to recommend the branch that fits best.

## ✨ Features

- 🎓 Input form capturing academic scores, interests and skills
- 🤖 ML-powered branch recommendation in seconds
- 📊 Model accuracy of **~87%** on held-out test data
- 💾 Responses stored in MongoDB for analysis and retraining
- 🌐 Deployed live on Render, no setup needed to try it

## 🧠 The ML Model

| Item | Details |
|---|---|
| Algorithm | Random Forest Classifier (scikit-learn) |
| Task | Multi-class classification (recommended branch) |
| Accuracy | **~87%** |
| Pipeline | Data cleaning → encoding → train/test split → training → evaluation → serialization |

**How it works:**

```
Student input → Preprocessing & encoding → Random Forest model → Recommended branch
                                                                       ↓
                                                             Stored in MongoDB
```

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python |
| Web framework | Flask |
| ML | scikit-learn, pandas, NumPy |
| Database | MongoDB |
| Frontend | HTML, CSS, JavaScript (Jinja templates) |
| Deployment | Render |

## 🚀 Run Locally

**Prerequisites:** Python 3.9+, pip, and a MongoDB instance (local or Atlas).

```bash
# 1. Clone the repository
git clone https://github.com/vaiii05/Branch-Fit.git
cd Branch-Fit

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
```

**Environment variables:** create a `.env` file in the project root:

```env
MONGO_URI=your_mongodb_connection_string
SECRET_KEY=your_secret_key
```

**Start the app:**

```bash
python app.py
```

Open **http://127.0.0.1:5000** 🎉

## 📁 Project Structure

```
Branch-Fit/
├── app.py              # Flask application and routes
├── model/              # Trained Random Forest model and training code
├── templates/          # HTML templates
├── static/             # CSS, JS, images
├── requirements.txt
└── README.md
```

<!--
## 📸 Screenshots
Add images to a docs/ folder, then uncomment:

| Input Form | Recommendation |
|---|---|
| ![Form](docs/form.png) | ![Result](docs/result.png) |
-->

## 🗺️ Roadmap

- [ ] Add explainability: show which factors drove each recommendation
- [ ] Expand the dataset and compare against Gradient Boosting and XGBoost
- [ ] Show top-3 branches with confidence scores
- [ ] Add a feedback loop to retrain on real outcomes

## 👥 Team

Built as a group mini project at Fr. CRIT, Vashi.

- **Vaibhavi Rai** ([@vaiii05](https://github.com/vaiii05))
- **Ashley Fernandes** ([@morethanashley](https://github.com/morethanashley))
- **Shivam Kshirsagar**
- **Ishwari Shinde** ([@Ishwari2010](https://github.com/Ishwari2010))

## 📬 Contact

**Vaibhavi Rai** · [GitHub](https://github.com/vaiii05) · [LinkedIn]([https://linkedin.com/in/your-id](https://www.linkedin.com/in/vaibhavi-rai-2b6110357/)) · vaibhavii.0515@gmail.com

---
<div align="center">⭐ If you found this useful, give it a star!</div>
