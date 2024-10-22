# CNN-Based Image Classification with DVC and CI/CD
This project is a CNN-based Image Classifier that leverages TensorFlow for training and classifying images. The classifier is integrated with DVC (Data Version Control) for efficient dataset management and model versioning, and CI/CD pipelines are implemented using GitHub Actions for continuous integration and delivery. The primary dataset consists of chicken fecal images for detecting health conditions.


## Table of Contents
- Project Overview
- Features
- Project Structure
- Technologies Used
- Dataset
- Setup Instructions
- How to Use
- Future Enhancements
- License

## Features
- Convolutional Neural Network (CNN) for image classification.
- DVC Integration for dataset version control and experiment tracking.
- CI/CD Pipelines using GitHub Actions for continuous integration and deployment.
- Dockerized Application for easy deployment on cloud platforms like AWS or Azure.
- Automated Model Evaluation with evaluation metrics like loss and accuracy stored in JSON files.

## Project structure
```bash
cnn_image_classifier/
│
├── .dvc/                         # DVC configuration files
├── .github/workflows/main.yaml    # CI/CD workflow for GitHub Actions
├── artifacts/                     # Model artifacts and data ingestion outputs
├── config/                        # Configuration files for model training
├── research/                      # Jupyter notebooks for experiments
├── src/
│   └── cnnClassifier/
│       └── components/            # Core components like data ingestion, model training, etc.
│       └── pipeline/              # Pipeline scripts for data ingestion, model training, evaluation
│       └── config/                # Configuration management for pipelines
│       └── utils/                 # Utility functions for common tasks
│
├── templates/                     # HTML templates for the web interface
├── app.py                         # Flask web application to serve the model
├── Dockerfile                     # Dockerfile for containerizing the app
├── dvc.yaml                       # DVC pipeline stages
├── params.yaml                    # Model parameters
├── requirements.txt               # Python dependencies
└── README.md                      # Project documentation (this file)
```

## Dataset
The dataset used for training the model is a set of chicken fecal images that are classified into two categories: Healthy and Coccidiosis.

- Source: [Chicken Fecal Images Dataset](https://github.com/diyorarti/datasets/raw/main/Chicken-fecal-images.zip)

## Setup Instructions
1. Clone the repository
```bash
git clone https://github.com/yourusername/cnn-image-classifier.git
cd cnn-image-classifier
```
2. Install dependencies
Make sure you have Python 3.8+ installed. Then, install the required dependencies:
```bash
pip install -r requirements.txt
```
3. Set up DVC
Make sure you have DVC installed and configured with your remote storage (e.g., AWS S3, Google Drive).
```bash
dvc pull
```
4. Train the model
You can run the model training pipeline by executing the following DVC command:
```bash
dvc repro
```
Alternatively, you can use the provided main.py script to run the entire pipeline:
```bash
python main.py
```
5. Run the web application
To start the Flask web application, use the following command:
```bash
python app.py
```
The app will run on http://localhost:80. Open this URL in your browser to interact with the web interface.

6. Docker Deployment
To build and run the application in Docker, use the following commands:
```bash
docker build -t cnn-image-classifier .
docker run -p 8080:80 cnn-image-classifier
```

## How to Use
1. **Train the Model**: Run the model training pipeline either with DVC or by executing the provided scripts.
2. **Deploy the App**: Use Docker to deploy the app locally or on a cloud platform like AWS or Azure.
3. **Interact with the Classifier**: Use the web interface or REST API to upload images and get predictions.


## Future Enhancements
- Model Tuning: Improve the CNN architecture and tune hyperparameters for better accuracy.
- Real-time Deployment: Deploy the classifier in real-time on cloud platforms like AWS ECS or Azure.
- Multi-class Classification: Expand the model to classify more health conditions beyond the current two categories.
- Data Augmentation: Implement more data augmentation techniques for improving model robustness.

