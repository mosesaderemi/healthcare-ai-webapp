# Healthcare AI Web App

A Flask web application that offers machine learning based risk screening for six conditions: diabetes, heart disease, kidney disease, liver disease, stroke and pneumonia. Users fill in a clinical form (or upload a chest X-ray for pneumonia) and receive a model prediction.

This project is for learning and demonstration. It is not a medical device and must not be used to diagnose or treat any condition.

## Features

- Landing page with an information page and a form page for each condition
- Tabular risk models for diabetes, heart disease, kidney disease, liver disease and stroke (scikit-learn and XGBoost, loaded from pickle files, with scalers for diabetes and stroke)
- Chest X-ray classification for pneumonia with a Keras deep learning model
- Image upload endpoint with filename sanitising
- Contact form that stores messages in SQLite
- Docker support

## Tech Stack

| Area | Technology |
| --- | --- |
| Backend | Python 3.8, Flask 2.0, Flask-SQLAlchemy |
| Machine learning | scikit-learn 0.24, XGBoost, TensorFlow CPU 2.6 and Keras |
| Database | SQLite |
| Frontend | Jinja2 templates, HTML, CSS, JavaScript |
| Deployment | Docker, Gunicorn |

## Project Structure

```text
.
├── app.py                    Application entry point
├── Dockerfile
├── requirements.txt
└── website
    ├── __init__.py           App factory and database setup
    ├── views.py              Page routes for each condition
    ├── prediction.py         /predict and /upload routes
    ├── app_functions.py      Model loading and prediction helpers
    ├── messages.py           Contact form route (/msg)
    ├── models.py             Messages table
    ├── app_models            Trained model files (.pkl and .h5)
    ├── templates             HTML templates
    ├── static                CSS, JavaScript, images
    └── uploads               Uploaded X-ray images (not stored in Git)
```

## Getting Started

### Prerequisites

- Python 3.8 (the pinned TensorFlow 2.6 and NumPy 1.19 versions do not install on newer Python releases)
- Docker, if you prefer containers

### Run locally

```bash
git clone https://github.com/mosesaderemi/healthcare-ai-webapp.git
cd healthcare-ai-webapp
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
flask run
```

Open `http://127.0.0.1:5000`. The SQLite database is created automatically on first start.

### Run with Docker

```bash
docker build -t healthcare-ai-webapp .
docker run -p 5000:5000 healthcare-ai-webapp
```

## Notes

- Model quality depends on the datasets the models were trained on and has not been clinically validated.
- Uploaded images and the `database.db` file are excluded from the repository.

## Author

Aderemi Moses Timileyin
GitHub: [@mosesaderemi](https://github.com/mosesaderemi)
LinkedIn: [linkedin.com/in/mosesaderemi-6a70a5405](https://www.linkedin.com/in/mosesaderemi-6a70a5405)

## License

Released under the MIT License. See the `LICENSE` file for details.
