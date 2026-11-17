# MLOps P08 – Delivery Time Prediction

## Project Overview

This project demonstrates how to package and deploy a Machine Learning model as a Dockerized API.

The application predicts food delivery time based on:
- Distance (km)
- Preparation time (minutes)
- Traffic level
- Rain condition

A Linear Regression model is trained and served through a FastAPI application. Docker is used to containerize the application and make it easier to run across different environments.

## Technologies Used

- Python 3.12
- NumPy
- Pandas
- Scikit-learn
- FastAPI
- Uvicorn
- Joblib
- Docker

## Project Structure

```text
MLOps-P08-Delivery-Prediction/
│
├── work/
│   ├── app.py
│   ├── model.joblib
│   ├── requirements.txt
│   ├── Dockerfile
│   ├── .dockerignore
│   ├── Dockerfile.v2
│   └── .dockerignore.mine
│
├── P08_S24CSEU2750.ipynb
└── docker-image-screenshot.png
```

## Model Information

The project uses a Linear Regression model to predict food delivery time.

### Input Features

| Feature | Description |
|---|---|
| distance_km | Delivery distance in kilometres |
| prep_time_min | Food preparation time in minutes |
| traffic_level | Traffic level (1–3) |
| rain | Rain condition (0 or 1) |

## Running the Project Using Docker

### 1. Build the Docker Image

```bash
docker build -t delivery-api:1.0 work
```

### 2. Run the Docker Container

```bash
docker run -d --name delivery-lab -p 8010:8000 delivery-api:1.0
```

### 3. Check the Application

Health endpoint:

```text
http://localhost:8010/health
```

Interactive API documentation:

```text
http://localhost:8010/docs
```

## API Endpoints

### GET /health

Checks whether the API is running.

### POST /predict

Accepts delivery details and returns the predicted delivery time.

Example request:

```json
{
  "distance_km": 5.0,
  "prep_time_min": 20,
  "traffic_level": 2,
  "rain": 0
}
```

Example response structure:

```json
{
  "delivery_min": 35.0,
  "model_version": "1.0"
}
```

*The predicted value will depend on the trained model.*

## Docker Image

Docker image created:

```text
delivery-api:1.0
```

The Docker image build and size verification are documented in `docker-image-screenshot.png`.

## Learning Outcomes

- Training and saving a Machine Learning model.
- Building a REST API using FastAPI.
- Creating a Dockerfile.
- Building and running Docker images and containers.
- Testing API endpoints.
- Understanding containerization in an MLOps workflow.

---

**Course:** MLOps – Practical 08  
**Project:** Delivery Time Prediction  
**Student:** Anjali Rathi  
**Roll Number:** S24CSEU2750
