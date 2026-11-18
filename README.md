# Air Quality Index (AQI) Predictor 🌍🍃

An end-to-end Machine Learning web application that predicts Air Quality Index (AQI) based on environmental pollutants and weather factors using Polynomial Regression models (Degree 3 and Degree 4).

Deployed with **Flask** and **Gunicorn**, ready for **Render** and **GitHub**.

---

## 📁 Project Structure

```text
Aqi predictor/
├── data/
│   └── aqi_prediction_dataset.csv   # Historical AQI dataset for training
├── notebooks/
│   └── aqi.ipynb                    # Data analysis & model training notebook
├── static/
│   └── css/                         # Static CSS/styling assets
├── templates/
│   └── index.html                   # Responsive frontend interface
├── .gitignore                       # Ignored files (venv, cache, system files)
├── .python-version                  # Python runtime version for Render (3.14)
├── app.py                           # Flask backend web application
├── aqi_model.pkl                    # Serialized ML model & preprocessors
├── Procfile                         # Process command for PaaS platforms (Render)
├── render.yaml                      # Render Blueprint for automated deployment
├── requirements.txt                 # Project dependencies
└── README.md                        # Documentation
```

---

## 🚀 Features

- **Polynomial Regression Models**: Compares predictions between Degree 3 and optimized Degree 4 polynomial regression.
- **Pollutants & Weather Factors**: Predicts AQI using 11 parameters:
  - Particulate Matter (`PM2.5`, `PM10`)
  - Gases (`NO2`, `SO2`, `CO`, `O3`)
  - Environmental factors (`Dust`, `Temperature`, `Humidity`, `Wind Speed`, `Rain`)
- **Real-Time AQI Categorization**: Categorizes AQI into Good, Satisfactory, Moderate, Poor, Very Poor, and Severe according to standard AQI scale.
- **Interactive UI**: Clean, responsive web design with input validation and out-of-range warnings.

---

## 💻 Local Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd "Aqi predictor"
```

### 2. Create and activate a virtual environment
```bash
# macOS/Linux
python3 -m venv venv
source venv/bin/activate

# Windows
python -m venv venv
venv\Scripts\activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the application
```bash
python app.py
```
Or with Gunicorn:
```bash
gunicorn app:app
```
Open [http://localhost:10000](http://localhost:10000) (or the port displayed in terminal) in your browser.

---

## ☁️ Deployment on Render

### Method 1: Automatic Blueprint (Recommended)
1. Push this repository to your **GitHub** account.
2. Sign in to [Render](https://render.com).
3. Click **New +** > **Blueprint**.
4. Select your GitHub repository. Render reads `render.yaml` automatically and configures:
   - **Environment**: Python
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app`
5. Click **Apply** to deploy.

### Method 2: Manual Web Service
1. On Render Dashboard, click **New +** > **Web Service**.
2. Connect your GitHub repository.
3. Configure settings:
   - **Name**: `aqi-predictor`
   - **Language**: `Python 3`
   - **Branch**: `main`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app`
4. Click **Deploy Web Service**.
