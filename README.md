# Insurance Premium Prediction API

This project is a **FastAPI-based web service** for predicting insurance premium categories using a trained machine learning model. The API receives user data (such as age, BMI, city, income, etc.), processes it, and returns a predicted insurance premium category.

---

## Features

- **REST API** built with FastAPI
- **Machine Learning Model** (scikit-learn) for prediction
- **Dockerized** for easy deployment
- **Input validation** using Pydantic schemas
- **Health check** and root endpoints
- Ready for deployment on any cloud or container platform

---

## Project Structure

```
Lecture-8-Insurance Premium Prediction Model/
│
├── app.py                      # Main FastAPI application
├── model/
│   ├── model.pkl               # Trained ML model (pickle file)
│   └── predict.py              # Model loading and prediction logic
├── schema/
│   ├── user_input.py           # Pydantic schema for input validation
│   └── prediction_response.py  # Pydantic schema for prediction response
├── requirements.txt            # Python dependencies
├── Dockerfile                  # Docker build instructions
└── README.md                   # Project documentation
```

---

## API Endpoints

### `GET /`
- **Description:** Human-readable welcome or info page.

### `GET /health`
- **Description:** Machine-readable health check endpoint. Returns API status.

### `POST /predict`
- **Description:** Predicts the insurance premium category.
- **Request Body:** JSON matching the `UserInput` schema (see below).
- **Response:** JSON with the predicted category.

---

## Example Request/Response

### Request

```json
POST /predict
Content-Type: application/json

{
  "age": 35,
  "bmi": 24.5,
  "city": "Delhi",
  "income_lpa": 10,
  "lifestyle_risk": "medium",
  "occupation": "Engineer"
}
```

### Response

```json
{
  "predicted_category": "medium"
}
```

---

## Setup & Usage

### 1. Clone the Repository

```sh
git clone <your-repo-url>
cd "Lecture-8-Insurance Premium Prediction Model"
```

### 2. Install Dependencies (Locally)

```sh
pip install -r requirements.txt
```

### 3. Run the API (Locally)

```sh
uvicorn app:app --reload
```
Visit [http://localhost:8000/docs](http://localhost:8000/docs) for the interactive Swagger UI.

---

## Docker Usage

### 1. Build the Docker Image

```sh
docker build -t karandevworks/insurance-premium-api .
```

### 2. Run the Docker Container

```sh
docker run -p 8000:8000 karandevworks/insurance-premium-api
```

Visit [http://localhost:8000/docs](http://localhost:8000/docs) to test the API.

---

## Requirements

- Python 3.8+
- See `requirements.txt` for all dependencies

---

## Notes

- **Model Compatibility:** Ensure the `model.pkl` file is compatible with your installed `scikit-learn` version.
- **MySQL Support:** If you use MySQL features, ensure the database is accessible and credentials are set.
- **Windows-only Packages:** This project is designed for Linux containers; Windows-only packages (like `pywin32`) are not included.
