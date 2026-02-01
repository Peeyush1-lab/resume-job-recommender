# 🎯 Resume Based Job Recommender
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-red.svg)](https://streamlit.io/)
[![ML](https://img.shields.io/badge/Machine%20Learning-Scikit--learn-orange.svg)](https://scikit-learn.org/)
[![GenAI](https://img.shields.io/badge/GenAI-HuggingFace-yellow.svg)](https://huggingface.co/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)<br><br>
![GitHub stars](https://img.shields.io/github/stars/Peeyush1-lab/resume-job-recommender?style=social)
![GitHub forks](https://img.shields.io/github/forks/Peeyush1-lab/resume-job-recommender?style=social)
![GitHub issues](https://img.shields.io/github/issues/Peeyush1-lab/resume-job-recommender)
![GitHub pull requests](https://img.shields.io/github/issues-pr/Peeyush1-lab/resume-job-recommender)
![GitHub last commit](https://img.shields.io/github/last-commit/Peeyush1-lab/resume-job-recommender)

> An intelligent AI-powered system that analyzes resumes to predict job roles, estimate salaries, identify skill gaps, and generate personalized career roadmaps.


## 🌟 Features


| <strong style="font-size: 20px;">Core functionality</strong>  | <strong style="font-size: 20px;">Description</strong>  |
|---|---|
| 📄 **Smart Resume Parser** | Upload PDF/DOCX or enter details manually |
| 🤖 **AI Job Prediction**  | ML-powered role recommendations (56+ job roles) |
| 💰 **Salary Forecasting** | Predict expected salary for each role |
| 📊 **Skill Gap Analysis** | Identify missing skills with match percentage |
| 🗺️ **AI Roadmaps**        | Get personalized career paths via GenAI |


### Key Highlights
- **Dual Input**: Resume upload (auto-extraction) or manual entry
- **Multi-label Classification**: Logistic Regression with 2000 iterations
- **Linear Regression**: Experience-based salary prediction
- **Visual Results**: Progress bars, sorted rankings, best match highlighting
- **Real-time Generation**: AI-powered roadmaps using HuggingFace API


## 🚀 Quick Start

Follow these steps to set up and run the Resume Job Recommender locally.

### 1. Clone the Repository
`git clone https://github.com/peeyush1-lab/resume-job-recommender.git`
> cd resume-job-recommender

### 2. Create and Activate a Virtual Environment
- `python -m venv .env`
- `source .env/bin/activate`    # On Windows: .env\Scripts\activate

### 3. Install Dependencies
> pip install -r requirements.txt

### 4. Configure Environment Variables
**Create a `.env` file and add your Hugging Face API key:**
> GENAI_API_KEY="your_huggingface_key"

### 5. Train the Models (Optional)
Run these scripts if the models are not already trained:

>  python role_prediction.py<br>
> python salary_prediction.py

### 6. Launch the Application
streamlit run main.py


**Access at:** `http://localhost:8501`

## 📦 Installation Requirements
> Run this command `pip install -r requirements.txt`


**Get HuggingFace API Key:** [https://huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)


## 💻 How to Use

### Method 1: Upload Resume
1. Select **"Upload Resume"**
2. Upload PDF/DOCX file (auto-extracts skills, education, experience)
3. Click **"Predict"**
4. View job matches, salaries, skill gaps, and match percentages

### Method 2: Manual Input
1. Select **"Choose Manual Inputs"**
2. Pick skills from dropdown (500+ options, add custom ones)
3. Choose education and set experience (slider: 0-40 years)
4. Click **"Predict"**
5. Get instant recommendations

### Generate Roadmap
- Select any predicted job role from dropdown
- AI generates personalized learning path with skills, courses, and timeline

## 🏗️ Project Structure

```
Resume_Based_Job_Recommender/
│
├── Dataset/
│   ├── Assets/
│   │   ├── masterskills.py              # 500+ skills database
│   │   └── AssigningJobRoles.py         # Job mappings
│   ├── Processesd Dataset/
│   │   ├── Final.csv                    # Training data
│   │   └── Final_salary.csv             # Salary data
│   └── Scraped Dataset/
│       ├── rolesdataset.csv
│       ├── salary.data.csv
│       ├── data_cleaning.py
│       └── data_cleaning_salary.py
│
├── Models/
│   ├── Assets/
│   │   ├── role_column.py               # 56 job roles
│   │   └── requiredjobskill.py          # Skills per role
│   ├── role_prediction.pkl
│   └── salary_prediction.pkl
│
├── main.py                               # Streamlit app
├── models.py                             # ML predictions
├── apicall.py                            # GenAI integration
├── resume_data_extract.py                # Resume parser
├── role_prediction.py                    # Model training
├── salary_prediction.py                  # Salary training
├── requirements.txt
├── .env                                  # API keys
└── README.md
```

## 🎯 Workflow

```
┌─────────────────────────────────────────────────────────┐
│  User Input: Resume Upload OR Manual Entry              │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│  Data Processing:                                       │
│  • Extract text (PyPDF2)                                │
│  • Parse skills, education, experience (Regex)          │
│  • Encode skills to binary vector                       │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│  ML Prediction:                                         │
│  • Job roles (Logistic Regression, score >0.5)          │
│  • Salaries (Linear Regression per role + exp)          │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│  Analysis & Display:                                    │
│  • Calculate skill gaps                                 │
│  • Compute match percentages                            │
│  • Sort by salary (highest first)                       │
│  • Show progress bars                                   │
│  • Highlight best match                                 │
└────────────────────┬────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────┐
│  AI Roadmap (Optional):                                 │
│  • User selects job role                                │
│  • GenAI generates personalized path                    │
└─────────────────────────────────────────────────────────┘
```
## 🛠️ Key Technologies

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Frontend** | Streamlit | Interactive web GUI |
| **Resume Parsing** | PyPDF2, Regex | Text extraction & pattern matching |
| **Job Prediction** | Logistic Regression | Multi-label classification (56 roles) |
| **Salary Prediction** | Linear Regression | Experience-based forecasting |
| **AI Roadmaps** | HuggingFace API | Career path generation |
| **Data Processing** | Pandas, NumPy | Dataset handling |
| **Model Storage** | Joblib | Serialization |

## 📊 Example Output

```
### Data Scientist
Expected Salary: $95,000
Your Skill Gap: [Deep Learning, NLP, TensorFlow]
Match Percentage: 87.5%
██████████████████░░ 87.5%

### Machine Learning Engineer
Expected Salary: $92,000
Your Skill Gap: [Kubernetes, Docker, MLOps]
Match Percentage: 82.3%
█████████████████░░░ 82.3%

### Data Analyst
Expected Salary: $75,000
Your Skill Gap: [Tableau, Power BI]
Match Percentage: 91.2%
████████████████████ 91.2%

🏆 Best Match: Data Analyst
```

---

## ⚙️ Configuration

### Environment Variables (`.env`)
```env
GENAI_API_KEY=hf_your_huggingface_token_here
```

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| **Resume upload fails** | Ensure PDF is text-based (not scanned), max 5MB |
| **API key error** | Verify `.env` has `GENAI_API_KEY=hf_...` |
| **Models not found** | Run `python role_prediction.py` and `python salary_prediction.py` |
| **Port already in use** | Use `streamlit run main.py --server.port 8502` |
| **Skills not detected** | Ensure skills match `masterskills.py` list or use manual input |
| **Module not found** | Run `pip install -r requirements.txt --force-reinstall` |

## 🤝 Contributing

Contributions welcome! Here's how:

1. Fork the repository
2. Create feature branch: `git checkout -b feature/AmazingFeature`
3. Commit changes: `git commit -m 'Add AmazingFeature'`
4. Push to branch: `git push origin feature/AmazingFeature`
5. Open Pull Request

**Ideas:** Resume builder, interview prep, job tracker, LinkedIn integration, visualization dashboard

## 🚀 Future Roadmap

- [ ] Real-time job market data integration
- [ ] Resume improvement suggestions
- [ ] Interview question generator
- [ ] LinkedIn profile analyzer
- [ ] Cover letter generator
- [ ] User authentication & history
- [ ] Mobile app (iOS/Android)
- [ ] Integration with job boards (Indeed, LinkedIn)
- [ ] Certification recommendations
- [ ] Salary negotiation tips

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 📧 Contact

- **GitHub:** [Peeyush1-lab](https://github.com/Peeyush1-lab)
- **Email:** tiwari.peeyush2006@gmail.com
- **Issues:** [Report Bug](https://github.com/Peeyush1-lab/resume-job-recommender/issues)


## 🙏 Acknowledgments

- **Streamlit** - Web framework
- **Scikit-learn** - ML tools
- **HuggingFace** - GenAI API
- **PyPDF2** - PDF parsing
- **Python Community** - Libraries & support

## 💡 Pro Tips

**For Best Results:**
- Use text-based PDFs (not scanned images)
- List skills explicitly in resume
- Include clear experience section ("5 years")
- Select all relevant skills in manual mode
- Choose specific job roles for roadmaps

**Security:**
- ✅ No data stored on servers
- ✅ Session-based processing
- ✅ API keys in `.env` (never commit)
- ✅ Local ML inference



<div align="center">

**⭐ Star this repo if helpful! ⭐**

Made with ❤️ for job seekers worldwide

[⬆ Back to Top](#resume-based-job-recommender)

</div>