# Smart Injury Analysis & Care - Final Documentation

## Overview
Smart Injury Analysis & Care is a web-based machine learning application that assists users in identifying and managing common injuries through image analysis. It classifies the injury type using a deep learning model and generates personalized care instructions, including precautions and recommended medications. The platform also provides downloadable PDF reports and a user-friendly interface for accessibility.

## Features
- **Injury Image Analysis**: Upload or capture images of injuries for CNN-powered classification.
- **Cropped Injury Visualization**: Automatically detects and crops the region of injury before classification.
- **Personalized Treatment**: Generates dynamic precautions and medication suggestions based on the injury type and user description.
- **PDF Report Generation**: Produces a visually formatted, downloadable injury report with precautions, medications, and image.
- **Responsive Design**: Compatible with desktop, tablet, and mobile devices.
- **Intuitive Interface**: Clean, minimalistic UI with clear workflows and immediate feedback.

## Technical Implementation

### Frontend
- HTML5, CSS3, and JavaScript for responsive design.
- Bootstrap-based card layout with intuitive file upload interface.
- Preview of uploaded image and cropped result.
- AJAX calls for real-time response from prediction API.

### Backend
- **Flask** (Python) for handling server logic and routing.
- **OpenCV** for image preprocessing, grayscale conversion, thresholding, contour detection, and region cropping.
- **TensorFlow/Keras** for CNN-based model inference.
- **NumPy** for array processing and data manipulation.
- **ReportLab** for generating professional injury assessment PDFs.
- RESTful API endpoints for:
  - Injury prediction (`/api/predict`)
  - PDF report download (`/api/download-report`)

### Machine Learning
- **Model Type**: Convolutional Neural Network (CNN) built using `TensorFlow/Keras`.
- **Classes**: Abrasion, Bruise, Burn, Cut, Ulcer.
- **Training**: Trained on a labeled injury image dataset using data augmentation and validation split.
- **Input Size**: 224x224 images normalized to [0, 1] range.
- **Output**: Softmax probabilities with highest class selected as prediction.
- **Model File**: `injury_model.h5` and corresponding `class_names.npy`.

## Pages

### Home
Introductory landing page describing the app's capabilities with links to other sections.

### Assess Injury
Main functional interface where users can:
1. Upload an injury image or capture via webcam.
2. Automatically detect and crop the injured area.
3. Predict injury type using CNN model.
4. View precautions, medication advice.
5. Download the PDF report for medical reference.

### Guidelines
Provides general education on injury types, treatment basics, and when to seek professional help.

### About
Describes project goals, technology used, and the AI model pipeline.

### Camera Access
- Webcam works on browsers with user permission enabled.
- May not function in some development environments due to browser sandboxing.
- Proper error handling implemented for permission denial.

### Image Upload
- Accepts PNG, JPG, JPEG formats only.
- Preview shown before analysis.
- Automatically processes and crops injury region before prediction.

### Prediction API
- Input image is processed, resized to 224x224, and passed to the CNN model.
- Returns JSON with:
  - Injury type
  - Confidence score
  - Cropped image (base64)
  - Precautions and medications
  - PDF report link
- Handles unexpected errors gracefully with informative responses.

### Prerequisites
- Python 3.9.11
- Flask, TensorFlow, OpenCV, ReportLab, NumPy
- Web server with WSGI support (for production deployment)

### Local Development Setup
1. Clone the repository
2. Create virtual environment: `python -m venv venv`
3. Activate the environment:
   - Windows: `venv\Scripts\activate`
   - Unix/MacOS: `source venv/bin/activate`
4. Install dependencies: `pip install flask opencv-python numpy tensorflow keras reportlab`
5. Start the server: `python app.py`
6. Visit `http://localhost:5000` in your browser

## Future Enhancements
- Enable user authentication for storing injury history and past reports.
- Expand injury classification to include sub-types and severity levels.
- Incorporate real-time video injury detection for athletes and clinics.
- Build a dedicated mobile application for field use and offline access.
- Enable AI-powered telemedicine chat to connect users with doctors.
- Improve model explainability with Grad-CAM visualizations.
