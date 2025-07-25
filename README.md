# Network Security Project - Phishing Data

## Overview
Welcome to the **Network Security Project for Phishing Data** repository! This project is part of the *Complete MLOps Bootcamp With End to End Data Science Project* and demonstrates an end-to-end data science solution for detecting phishing data. It includes data processing, model training, prediction pipelines, and deployment on AWS EC2 using Docker and GitHub Actions.

## Project Description
This repository focuses on a cybersecurity application designed to identify phishing data. It leverages machine learning to analyze network data, with a deployment pipeline containerized using Docker and hosted on AWS EC2, automated via GitHub Actions.

## Features
- **Environment Setup**: Uses Anaconda with Python 3.10 for virtual environment management.
- **Project Structure**: Includes `network_data` (for datasets), `notebooks`, and `network_security` (with subfolders like `components`, `constants`, `entity`, `exception`, `logging`, `pipeline`, `utils`, and `cloud`).
- **Version Control**: Managed with Git and GitHub.
- **Deployment**: Containerized with Docker and deployed on AWS EC2 using GitHub Actions CI/CD pipelines.
- **Logging & Exception Handling**: Custom logging and exception classes for error management.
- **Prediction Pipeline**: Flask-based web application for real-time phishing detection using pickle files.

## Getting Started

### Prerequisites
- Python 3.10
- Anaconda
- Git
- Docker
- AWS CLI (configured with credentials)
- Basic understanding of Flask and machine learning concepts

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/network_security.git
   ```
2. Navigate to the project directory:
   ```bash
   cd network_security
   ```
3. Create and activate the virtual environment:
   ```bash
   conda create -p venv python=3.10
   conda activate venv
   ```
4. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Running the Project
1. Start the Flask application:
   ```bash
   python app.py
   ```
2. Access the web app at `http://127.0.0.1:5000/predict_data`.

### Deployment
- **GitHub Secrets Configuration**:
  Set the following secrets in your GitHub repository settings under "Secrets and variables" > "Actions":
  - `AWS_ACCESS_KEY_ID`: Your AWS access key ID
  - `AWS_SECRET_ACCESS_KEY`: Your AWS secret access key
  - `AWS_REGION`: `us-east-1`
  - `AWS_ECR_LOGIN_URI`: `788614365622.dkr.ecr.us-east-1.amazonaws.com/networkssecurity`
  - `ECR_REPOSITORY_NAME`: `networkssecurity`

- **Build the Docker Image**:
  ```bash
  docker build -t networkssecurity .
  ```

- **Docker Setup on EC2**:
  Execute the following commands on your EC2 instance:
  ```bash
  # Optional updates
  sudo apt-get update -y
  sudo apt-get upgrade

  # Required Docker installation
  curl -fsSL https://get.docker.com -o get-docker.sh
  sudo sh get-docker.sh
  sudo usermod -aG docker ubuntu
  newgrp docker
  ```

- **Push to ECR and Deploy**:
  Configure AWS CLI, push the image to ECR, and trigger GitHub Actions for deployment to EC2 (see `main.yml`).

## File Structure
```
network_security/
├── network_data/          # Phishing datasets
├── notebooks/             # Jupyter notebooks
├── network_security/      # Main package
│   ├── components/
│   ├── constants/
│   ├── entity/
│   ├── exception/
│   ├── logging/
│   ├── pipeline/
│   ├── utils/
│   └── cloud/
├── .gitignore             # Excludes venv and sensitive files
├── Dockerfile             # Docker configuration
├── requirements.txt       # Project dependencies
├── setup.py               # Package configuration
├── app.py                 # Flask web application
├── .github/workflows/     # GitHub Actions workflows
│   └── main.yml
└── README.md              # This file
```

## Contributing
Fork this repository, submit issues, or create pull requests. Contributions to enhance the phishing detection model, documentation, or deployment process are welcome!

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Inspired by the *Complete MLOps Bootcamp With End to End Data Science Project* course.
- Thanks to the open-source community for tools like Docker, Flask, and GitHub Actions.
