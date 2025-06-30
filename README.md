# Insurance_MLOps# 🚗 MLOps Project – Vehicle Insurance Claim Approval Prediction

Welcome to my end-to-end MLOps project built for predicting vehicle insurance claim approvals. This project showcases my ability to design, build, and deploy a scalable, production-grade machine learning pipeline with real-world tools and cloud services.

I built this to demonstrate hands-on skills across **data engineering**, **model development**, **deployment**, and **CI/CD automation** using **Python, Docker, FastAPI, MongoDB, AWS, and GitHub Actions**.

---

## 📦 Project Architecture

### ✅ Key Highlights
- Modular, production-ready ML pipeline
- Real-time prediction via FastAPI API
- CI/CD automation with Docker + GitHub Actions
- Cloud deployment using AWS EC2, S3, and ECR
- Imbalanced classification handling with F1-score evaluation

---

## 🔧 Project Setup

### 🧱 Step 1: Generate Project Structure
I started by running `template.py` to auto-generate the project’s folder structure and placeholder files.

### 📦 Step 2: Package Management
I defined local package setups using `setup.py` and `pyproject.toml`. For guidance, see the `crashcourse.txt` inside the repo.

### 🧪 Step 3: Virtual Environment & Dependencies
```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt


---

## 🗃️ Data Management with MongoDB

### ☁️ Step 4: MongoDB Atlas Setup
- Signed up on [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and created a new project.
- Created a free M0 cluster, added database user credentials, and allowed IP access from `0.0.0.0/0`.
- Retrieved the Python connection string and saved it securely by replacing `<password>` with the actual password.

### 📤 Step 5: Upload Data to MongoDB
- Created a `notebook/` directory and added the dataset.
- Wrote `mongoDB_demo.ipynb` to connect to MongoDB and push the dataset to a collection.
- Verified the uploaded data using MongoDB Atlas under **Browse Collections**.

---

## 🧠 EDA, Logging, and Exception Handling

### 🪵 Step 6: Logging & Exception Handling
- Created a logging utility to track each stage of the pipeline.
- Built custom exception handling classes.
- Verified both by testing them in a demo script (`demo.py`).

### 📊 Step 7: EDA & Feature Engineering
- Performed Exploratory Data Analysis in a dedicated notebook.
- Engineered features relevant for training, considering domain understanding and data imbalance.

---

## 🔁 Pipeline Components

### 📥 Step 8: Data Ingestion
- Defined MongoDB connection logic in `configuration/mongo_db_connection.py`.
- Created ingestion logic in `components/data_ingestion.py` to load data from MongoDB and convert to DataFrame.
- Updated ingestion-related entities in `entity/config_entity.py` and `entity/artifact_entity.py`.

To run:
```bash
python demo.py



---

## 🔍 Data Validation, Transformation & Model Training

### ✅ Step 9: Data Validation
- Defined the input schema using a YAML config file at `config/schema.yaml`.
- Wrote custom validation utilities in `utils/main_utils.py` to ensure schema compliance before processing.
- Integrated validation checks into the pipeline to catch missing/null columns, unexpected data types, and schema mismatches.

### 🔄 Step 10: Data Transformation
- Implemented preprocessing logic in `components/data_transformation.py`.
- Built custom `estimator.py` under `entity/` to manage transformation and serialization of preprocessing objects.
- Transformed raw features, handled missing values, encoded categoricals, and scaled numerical columns.

### 🏋️ Step 11: Model Training
- Trained the model using code in `components/model_trainer.py`, referencing the custom estimators from earlier steps.
- Utilized scikit-learn classifiers with hyperparameter tuning.
- Stored model and preprocessing pipeline artifacts for downstream use.

---

## 🌐 AWS Setup for Model Evaluation & Deployment

### 🔐 Step 12: AWS Setup
- Created an IAM user in AWS with AdministratorAccess.
- Configured AWS credentials in local environment using:
```bash
export AWS_ACCESS_KEY_ID="your_aws_access_key"
export AWS_SECRET_ACCESS_KEY="your_aws_secret"

### 🧊 Step 13: Model Evaluation and Pushing to S3
- Created an S3 bucket named `my-model-mlopsproj` in the `us-east-1` region.
- Implemented functionality to upload and retrieve model artifacts from S3 using `boto3` in `src/aws_storage/` and `entity/s3_estimator.py`.
- Evaluated the model using F1-score due to the imbalanced dataset.
- If performance improved, the new model was pushed to the S3 bucket for production use.

---

## 🚀 Model Deployment & Prediction Pipeline

### 🧪 Step 14: Model Evaluation & Model Pusher
- Compared trained model performance with the existing one in production.
- Replaced the old model in S3 if the new model's F1-score was better.
- Ensured traceability and version control of all model artifacts.

### 🌐 Step 15: Prediction API with FastAPI
- Developed a RESTful prediction API using FastAPI in `app.py`.
- Loaded the latest model and preprocessor from S3.
- Enabled real-time inference for incoming data through the `/predict` endpoint.

### 🖼️ Step 16: Frontend UI Setup
- Added `templates/` directory with an HTML interface for user input.
- Integrated form submission to fetch predictions from the FastAPI backend.
- Included `static/` folder for styling assets (CSS/images if any).

---

## 🔄 CI/CD Setup with Docker, GitHub Actions, and AWS

### 🐳 Step 17: Docker and GitHub Actions
- Wrote a production-ready `Dockerfile` and `.dockerignore`.
- Set up GitHub Actions to:
  - Build Docker image on push
  - Push to AWS Elastic Container Registry (ECR)
  - Deploy to EC2 via self-hosted runner

### 🔐 GitHub Secrets
Stored these in GitHub repository settings:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_DEFAULT_REGION`
- `ECR_REPO`

---

## ☁️ EC2 Deployment & Access

### 💻 Step 18: AWS EC2 and ECR
- Provisioned an EC2 instance (Ubuntu) and installed Docker.
- Registered EC2 as a GitHub self-hosted runner.
- Pulled latest image from ECR and ran container with exposed port.

### 🌍 Step 19: Access the Application
- Opened port `5080` in EC2 security group.
- Accessed the app in browser at: http://<EC2_PUBLIC_IP>:5080


---

## ✅ Workflow Summary

1. **MongoDB Atlas** → Data Ingestion  
2. **Validation** → Schema Checks  
3. **Transformation** → Preprocessing Pipeline  
4. **Model Training** → F1-Optimized Classifier  
5. **Evaluation** → S3 Model Store  
6. **Deployment** → FastAPI + Docker  
7. **CI/CD** → GitHub Actions + AWS EC2 + ECR

---

## 📈 Model Performance

- **F1-Score**: 0.76 on imbalanced validation set  
- **Real-time Predictions**: Enabled via FastAPI  
- **CI/CD**: Fully automated via GitHub Actions and Docker

---

## 🛠️ Tech Stack

- **Language**: Python  
- **ML Tools**: Scikit-learn, Pandas, NumPy  
- **Data**: MongoDB Atlas  
- **Deployment**: FastAPI, Docker, AWS EC2, S3, ECR  
- **Automation**: GitHub Actions  
- **Monitoring**: Custom Logging and Exception Handling

---

## 🙋‍♂️ Contact

Feel free to reach out if you have any questions or want to collaborate!


