# 🌱 OptiCrop — Smart Agricultural Production Optimization Engine

OptiCrop is a web-based crop recommendation platform that helps farmers choose the
best crop for their land. A user enters soil and environmental parameters — Nitrogen,
Phosphorous, Potassium, Temperature, Humidity, pH, and Rainfall — and OptiCrop
recommends the most suitable crop along with expected yield, growing season, water
requirement, sunlight needs, and practical farming tips.

---

## ✨ Features

- **AI-powered crop recommendation** based on 7 soil/environmental parameters
- **21+ supported crops** (Rice, Wheat, Maize, Cotton, Sugarcane, Coffee, Tea, and more)
- Clean, responsive landing page with animated UI (Home, About, Find Your Crop, Results)
- Detailed results panel: expected yield, growing season, water & sunlight needs,
  AI confidence score, and farming tips
- Sign In / Sign Up modals
- Built with Flask and a pickled recommendation model (`model.pkl`), following the
  same load-and-predict pattern as a trained ML model

---

## 🛠️ Tech Stack

| Layer      | Technology                                  |
|------------|----------------------------------------------|
| Backend    | Python, Flask                                |
| Model      | Rule-based recommendation engine (`model.pkl`, loaded via `pickle`) |
| Frontend   | HTML5, CSS3, JavaScript (vanilla)            |
| Templating | Jinja2 (Flask `render_template`)             |
| Icons/Fonts| Font Awesome, Google Fonts (Poppins, Playfair Display) |

---

## 📁 Project Structure

```
OptiCrop/
│
├── app.py                  # Flask app, routes, and /predict endpoint
├── model.py                # CropModel class (recommendation logic)
├── model.pkl               # Pickled CropModel instance
├── requirements.txt        # Python dependencies
│
├── templates/
│   ├── base.html            # Shared layout: navbar, footer, modals
│   ├── home.html            # Landing page (hero, features, testimonials, CTA)
│   ├── about.html           # About the project
│   ├── findyourcrop.html    # Crop prediction form + results
│   ├── result.html          # Results & analytics overview
│   ├── signin.html          # Sign-in modal
│   └── signup.html          # Sign-up modal
│
└── static/
    ├── css/
    │   └── style.css        # All site styling
    ├── js/
    │   └── script.js        # Nav, modals, animations, scroll effects
    └── images/
        ├── home.jpg
        ├── about.jpg
        ├── findyourcrop.jpg
        └── result.jpg
```

---

## ⚙️ Installation & Setup

1. **Clone or download** the project folder.

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv venv
   venv\Scripts\activate        # Windows
   source venv/bin/activate     # macOS/Linux
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Add your images** to `static/images/`:
   - `home.jpg`, `about.jpg`, `findyourcrop.jpg`, `result.jpg`

5. **Run the app:**
   ```bash
   python app.py
   ```

6. Open your browser at **http://127.0.0.1:5000**

---

## 🔮 How Prediction Works

1. The user fills in the **Find Your Crop** form with 7 parameters, in this order:
   `Nitrogen → Phosphorous → Potassium → Temperature → Humidity → pH → Rainfall`
2. The form submits a standard `POST` request to `/predict`.
3. `app.py` collects the values, builds a feature array, and calls:
   ```python
   prediction = model.predict(features)
   output = prediction[0]   # e.g. "Rice (Paddy)"
   ```
4. The page re-renders with `prediction_text` (e.g. *"Best crop for given conditions is
   Rice (Paddy)"*) plus extra details — expected yield, season, water needs, sunlight
   needs, AI confidence score, and farming tips — pulled from `model.details(output)`.

---

## 🌐 Routes

| Route            | Method | Description                              |
|-------------------|--------|-------------------------------------------|
| `/`               | GET    | Home page                                 |
| `/about`          | GET    | About the project                         |
| `/findyourcrop`   | GET    | Crop recommendation form                  |
| `/predict`        | POST   | Runs the model and returns the prediction |
| `/result`         | GET    | Results & analytics overview page         |
| `/signin`         | POST   | Handles sign-in form submission           |
| `/signup`         | POST   | Handles sign-up form submission           |

---

## 🚀 Future Scope

- Replace the rule-based engine with a trained ML model (e.g. Random Forest / XGBoost)
  on a real agricultural dataset
- Add live weather API integration for real-time temperature and rainfall data
- User accounts with saved prediction history
- Multi-language support for regional farmers
- Mobile app version

---

## 👤 Author

Developed as part of an agricultural technology project — **OptiCrop: Smart
Agricultural Production Optimization Engine**.
