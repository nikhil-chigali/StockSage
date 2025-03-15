# StockSage: Predictive Analytics for Market Movements

## 🏗️ Project Structure
```
StockSage/
├── .github/                           # GitHub Actions CI/CD workflows
│   └── workflows/
│       ├── ci.yml                     # Continuous Integration workflow
│       └── cd.yml                     # Continuous Deployment workflow
│
├── data/                              # Datasets (versioned using DVC)
│   ├── raw/                           # Raw data files (initial ingestion)
│   ├── processed/                     # Processed data files (after Glue/Lambda transformations)
│   └── features/                      # Feature-engineered datasets
│
├── kafka/                             # Apache Kafka setup scripts & configs
│   ├── producer.py                    # Kafka producer script (simulate real-time data)
│   └── consumer.py                    # Kafka consumer script (ingest streaming data)
│
├── glue_jobs/                         # AWS Glue Interactive sessions & PySpark scripts
│   ├── preprocessing.py               # Data cleaning & preprocessing scripts
│   └── feature_engineering.py         # Feature engineering scripts
│
├── lambda_functions/                  # AWS Lambda functions for ingestion & inference
│   ├── ingestion_lambda/              # Lambda for ingesting Kafka data into S3
│   │   ├── lambda_function.py         
│   │   └── requirements.txt           
│   │
│   └── inference_lambda/              # Lambda for model inference serving via API Gateway
│       ├── lambda_function.py         
│       ├── Dockerfile                 # Containerized Lambda deployment (optional)
│       └── requirements.txt           
│
├── ml_pipeline/                       # ZenML pipelines definition & orchestration logic
│   ├── pipelines/
│   │   └── training_pipeline.py       # ZenML pipeline definition (training/evaluation)
│   │
│   ├── steps/
│   │   ├── ingest_data.py             # Data ingestion step from Kafka/S3
│   │   ├── preprocess_data.py         # Data preprocessing step integration with Glue/Athena
│   │   ├── train_model.py             # Model training step with scikit-learn & MLFlow logging
│   │   └── evaluate_model.py          # Model evaluation step with MLFlow logging 
│   │
│   └── run_pipeline.py                # Script to trigger ZenML pipeline execution locally/cloud
│
├── notebooks/                         # Jupyter notebooks for EDA, prototyping, visualizations
│   ├── exploratory_data_analysis.ipynb 
│   └── feature_engineering.ipynb      
│
├── models/                            # ML models artifacts (managed via MLFlow registry)
├── docker/                            # Dockerfiles for containerization across the pipeline stages
│   ├── training_env.Dockerfile        # Dockerfile for training environment (ZenML, MLFlow, etc.)
│   └── inference_env.Dockerfile       # Dockerfile for inference environment (AWS Lambda/Azure AI Studio)
│ 
├── deployments/                       # Deployment scripts & configurations for Azure/AWS endpoints 
│   ├── azure_ai_studio/
│   │    ├── deploy_model.py           # Azure AI Studio model deployment script 
│   │    └── azure_config.json         # Azure deployment configuration file 
|   |
|   └── aws_api_gateway/
|        ├── template.yaml             # AWS SAM or CloudFormation template for API Gateway/Lambda setup 
|        └── deploy.sh                 # Deployment automation script (SAM CLI or AWS CLI commands) 
|
├── src/                               # Common source code utilities and libraries used across the project 
|    └── utils/
|         ├── data_utils.py            # Data loading/saving helpers  
|         └── model_utils.py           # Model serialization/deserialization helpers  
|     
├─ configs/
|    └─ config.yaml                    # Centralized configuration parameters  
|
├── tests/                             # Unit tests and integration tests 
|    ├─ unit_tests/
|    |     └─ test_pipeline_steps.py   
|    |
|    └─ integration_tests/
|          └─ test_end_to_end.py       
|
├── .dockerignore                      # Docker ignore file to exclude unnecessary files from containers 
├── .gitignore                         # Git ignore file to exclude sensitive/unnecessary files from Git repo  
├── dvc.yaml                           # DVC pipeline definition file  
├── requirements.txt                   # Python dependencies for local development environment  
└─ README.md                           # Project documentation, setup instructions, architecture overview  
```
