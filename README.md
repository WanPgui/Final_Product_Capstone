Final Capstone Project Submission -  Mold-Kit Web App
Student Name: Peris Wangui
 Supervisor Name: Samiratu Ntohsi
 Date: December 1, 2025
 
 1. Project Title
Mold-Kit: A Machine Learning-Powered Web Application for Mold Detection

2. Project Repository & Demo Links
GitHub Repository
 https://github.com/WanPgui/Final_Product_Capstone
Demo Video https://drive.google.com/file/d/10NCNTWTqxIm82Ids1nxYJYpJ9KeC_OtH/view?usp=sharing
The repository includes:
Complete backend code (FastAPI + TensorFlow model)
Frontend UI hosted on Netlify
Model artifacts & training notebook
Fully updated code after panel feedback
Comprehensive README for deployment and installation
3. Project Overview
Mold-Kit is a lightweight yet powerful web application designed to detect mold from uploaded images using a trained Machine Learning model. The system enables users to upload a photo, optionally include environmental data (ventilation, humidity, water leaks), and instantly receive an AI-based mold risk assessment.
The system aims to help homeowners, renters, property managers, and building inspection teams detect early mold growth to prevent health issues and structural damage.
System Components
Frontend (Netlify): Interactive and mobile-responsive interface
Backend (Render): FastAPI-powered server for inference and API integration
AI Model: TensorFlow CNN, optimized for binary mold detection
4. Key Features
Drag-and-drop or manual file image upload
Optional metadata: location, ventilation, leak status
Real-time predictions with confidence levels
Color-coded results (green = clean, red = mold detected)
No page reload (AJAX async fetch)
Automatic image preprocessing and normalization
Swagger interactive documentation (/docs)
Clean, responsive, and mobile-friendly UI
5. Project Structure
Final_Product_Capstone/
├── Backend/
│   ├── main.py                  # FastAPI main application
│   ├── app.py                   # Helper functions + preprocessing
│   ├── model/
│   │   └── mold_model_final.keras
├── Database/
├── models/
│   └── mold_Prediction_(1).ipynb
├── static/                      # JS, CSS, images
├── templates/                   # HTML frontend files
└── README.md
6. Installation & Running the Project
Backend (FastAPI)
cd Backend
pip install -r requirements.txt
uvicorn main:app --reload
Server starts at:
 http://localhost:8000
Ensure that your model file exists at:
 Backend/model/mold_model_final.keras 
Frontend
Open index.html in any browser
 OR
Serve using a simple HTTP server:
python -m http.server 8001
Make sure the frontend POST request URL matches:
http://localhost:8000/predict 

7. How Mold-Kit Works (Pipeline)
User uploads an image and optionally fills environmental metadata.
Frontend sends a POST /predict request using FormData.
Backend:
Loads and preprocesses the image
Resizes to 224x224
Normalizes pixel values
Passes tensor into TensorFlow model
Model outputs probabilities → converted into label and confidence.
Response returned as JSON:
{
  "label": "Mold Detected",
  "confidence": 0.82,
  "risk": "High Risk"
}

8. API Endpoints & Testing Demo (Swagger / cURL / Postman)
Below are fully working demos of all exposed backend routes.
8.1 Swagger UI (Interactive Docs)
Navigate to:
 http://localhost:8000/docs
From here, you can:
Upload an image
Add location/ventilation/leak data
Make predictions
Validate response formats
Test without the frontend
8.2 Test Using cURL
POST /predict
Upload an image for prediction:
curl -X POST "http://localhost:8000/predict" \
  -H "accept: application/json" \
  -H "Content-Type: multipart/form-data" \
  -F "file=@test_image.jpg" \
  -F "location=Kitchen" \
  -F "ventilation=Poor" \
  -F "water_leak=true"
Expected Response
{
  "label": "Mold Detected",
  "confidence": 0.91,
  "risk": "High Risk"
}

GET /
Health check endpoint:
curl -X GET "http://localhost:8000/"
Response:
{"status": "API running successfully"}
8.3 Test Using Postman
Step-by-step
Open Postman → Click New Request
Set method to POST
Enter URL:
 http://localhost:8000/predict 
Go to Body → form-data
Add form fields:
file (type: File → choose image)
location (text)
ventilation (text)
water_leak (boolean or text)
Click Send
View JSON prediction result instantly
9. Future Improvements
Multi-class mold identification (green/black/white mold)
User profiles + prediction history
Batch image processing
Automated retraining with user-submitted photos
PDF report generation with cleaning recommendations
Admin dashboard for analytics and trends


10. Tech Stack
Component
Technology
Frontend
HTML, CSS, JavaScript
Backend
Python, FastAPI
ML Model
TensorFlow, Keras
Hosting
Netlify (frontend), Render (backend)
DB
SQLite 

11. Updates After Panel Feedback
Improved error handling in prediction endpoint
Explained preprocessing pipeline clearly in the documentation
Updated README to include full setup + deployment steps
Reorganized backend directory for clarity
Ensured consistent API responses
Added endpoint usage examples (cURL, Postman, Swagger)
12. Supervisor & Student Signatures
Student:  Peris Wangui  
Supervisor: Samiratu Ntohsi 
Date: 1-12-2025
