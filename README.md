# Final_Product_Capstone

Link to demo video: https://drive.google.com/file/d/10NCNTWTqxIm82Ids1nxYJYpJ9KeC_OtH/view?usp=sharing

Final_Product_Capstone - Mold-Kit  Web App
Overview
Mold-Kit is a web app that uses ML to detect mold from photos of surfaces. Users can upload images, optionally provide context like location, ventilation, and leaks, and instantly get a prediction — helping prevent health issues and structural damage.
The project is divided into two main components:
- Frontend: Hosted on Netlify for a responsive, user-friendly interface accessible on desktop and mobile devices.
- Backend: Hosted on Render, built with FastAPI and TensorFlow for real-time  predictions.
Mold-Kit aims to make mold detection accessible, accurate, and fast for homeowners, property managers, and building inspectors.
________________________________________
Features
•	Upload images via drag & drop or file selection

•	Optional input fields: location, ventilation, leaks

•	Real-time AI prediction with confidence score

•	Color-coded results for quick assessment (red = mold, green = clean)

•	Instant updates without page reload using asynchronous JavaScript

•	Swagger API docs for testing endpoints and developer integration

•	Responsive UI for desktop, tablet, and mobile

•	Temporary image storage and preprocessing to optimize model accuracy
________________________________________
Project Structure
Final_Product_Capstone/
├── Backend/                # FastAPI API + model handling
│   ├── app.py             #  Preprocessing and helper functions & Entry point for API routes
│   └── model/              # TensorFlow model files
├── Database/               # Optional metadata or user submission storage
├── models/                 # Model training artifacts and notebooks
│   └── mold_Prediction_ (1).ipynb # Notebook for building/testing the model
├── static/                 # Frontend CSS, JS, images
├── templates/              # HTML templates for the web interface
└── README.md               # Project documentation
________________________________________
Setup
1. Clone Repository
git clone https://github.com/WanPgui/Final_Product_Capstone.git
cd Final_Product_Capstone
2. Backend Setup
cd Backend
pip install -r requirements.txt
uvicorn main:app --reload
•	Ensure mold_model_final.keras is in the model/ folder.
•	Backend runs a FastAPI server at http://localhost:8000 by default.
3. Frontend Setup
•	Open index.html in a browser or serve via a local HTTP server.
•	Ensure frontend points to backend /predict endpoint (e.g., http://localhost:8000/predict).
________________________________________
How It Works
1.	User uploads an image and fills optional metadata.
2.	Frontend sends a POST /predict request to backend.
3.	Backend preprocesses the image, resizes it to 224x224 pixels, and normalizes it for the TensorFlow model.
4.	ML model returns a prediction JSON:
{
  "label": "Mold Detected",
  "confidence": 0.85,
  "status": "High Risk"
}
5.	Frontend displays results with confidence score and visual cue instantly.
Additional backend routes: - GET / — health check. - GET /docs — Swagger UI for API testing.
________________________________________
Future Work
•	Multi-class mold detection (black, green, white mold)
•	User accounts with prediction history and notifications
•	Improved mobile-first UI/UX and accessibility
•	PDF report generation with recommendations for remediation
•	Batch image upload support
•	Auto model retraining using new user-submitted images
•	Analytics dashboard to track common mold locations and risk trends
________________________________________
Tech Stack
•	Frontend: HTML, CSS, JavaScript
•	Backend: Python, FastAPI
•	AI/ML: TensorFlow, Keras
•	Hosting: Netlify (Frontend), Render (Backend)
•	Database support for metadata storage (SQLite)
________________________________________
Contact
Open an issue or reach out via GitHub for questions, suggestions, or contributions.
Early mold detection made simple, accurate, and accessible for everyone.
