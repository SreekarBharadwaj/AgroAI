# NLP Project: Named Entity Recognition and DeepSeek Implementation

## 🌱 Smart Agriculture Assistant

This application processes natural language input to extract key agricultural parameters and provide intelligent crop and fertilizer recommendations. It identifies the following parameters from user input:
- Temperature
- Humidity
- Moisture
- Soil Type
- Nitrogen levels
- Potassium levels
- Phosphorous levels

Using advanced Named Entity Recognition (NER) and DeepSeek model integration, the system analyzes these parameters to provide:
- Optimal crop recommendations
- Suitable fertilizer suggestions
- Agricultural best practices

This repository contains a comprehensive NLP project focusing on Named Entity Recognition (NER) and DeepSeek model implementation. The project includes training notebooks, testing scripts, and Flask-based web applications for deployment.

## Project Structure

```
nlp/
├── src/                    # Source code directory
│   ├── apps/              # Application code
│   │   ├── deepseek-app/  # DeepSeek model application
│   │   │   ├── app.py                    # Main DeepSeek application
│   │   │   ├── generate_response.py      # Response generation module
│   │   │   ├── Dockerfile               # Docker configuration
│   │   │   ├── deploy_docker.bat        # Deployment script
│   │   │   └── requirements.txt         # Python dependencies
│   │   └── ner-app/       # NER application
│   │       ├── app.py                    # Main NER application
│   │       ├── Dockerfile               # Docker configuration
│   │       ├── deploy_docker.bat        # Deployment script
│   │       ├── app.yaml                 # Google Cloud configuration
│   │       └── requirements.txt         # Python dependencies
│   ├── notebooks/         # Jupyter notebooks
│   │   ├── training/      # Training notebooks
│   │   │   ├── ner_training.ipynb           # NER model training
│   │   │   └── deepseek_finetuning.ipynb    # DeepSeek model fine-tuning
│   │   └── testing/       # Testing notebooks
│   │       ├── deepseek_test.ipynb          # DeepSeek model testing
│   │       ├── bert_test.ipynb              # BERT model testing
│   │       ├── ner_test.ipynb               # NER model testing
│   │       └── deepseek_ner_test.ipynb      # Integrated testing
│   └── models/            # Model files and configurations
│       ├── ner_model/                      # NER model files
│       └── deepseek_model/                 # DeepSeek model files
├── docs/                  # Documentation
│   ├── api/                               # API documentation
│   └── deployment/                        # Deployment guides
├── README.md             # Project documentation
├── LICENSE               # License file
└── .gitignore           # Git ignore file
```

## Features

- Named Entity Recognition (NER) implementation
- DeepSeek model integration
- Flask-based web applications for model deployment
- Training and testing notebooks
- Docker support for containerization
- Google Cloud deployment configuration

## Getting Started

### Prerequisites

- Python 3.8+
- pip
- Docker (for containerization)
- Google Cloud SDK (for deployment)
- Google Cloud account with billing enabled

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/nlp.git
cd nlp
```

2. Install dependencies for each application:
```bash
# For NER application
cd apps/ner-app
pip install -r requirements.txt

# For DeepSeek application
cd ../deepseek-app
pip install -r requirements.txt
```

## Deployment Instructions

### DeepSeek Application Deployment

1. Navigate to the DeepSeek application directory:
```bash
cd apps/deepseek-app
```

2. Deploy using the provided script:
```bash
deploy_docker.bat
```

The DeepSeek application will be deployed to Google Cloud Run with GPU support. The service URL will be:
```
https://deepseek-flask-gpu-service-742894389221.us-central1.run.app
```

### NER Application Deployment

1. Navigate to the NER application directory:
```bash
cd src/apps/ner-app
```

2. Deploy using the provided script:
```bash
deploy_docker.bat
```

The NER application will be deployed to Google Cloud Run and will automatically connect to the DeepSeek service using the configured URLs:
- Status URL: `https://deepseek-flask-gpu-service-742894389221.us-central1.run.app/status`
- Reload URL: `https://deepseek-flask-gpu-service-742894389221.us-central1.run.app/reload`
- Predict URL: `https://deepseek-flask-gpu-service-742894389221.us-central1.run.app/predict`

### Manual Docker Deployment

If you prefer to deploy manually:

1. Build the Docker image:
```bash
docker build -t nlp-app .
```

2. Run the container:
```bash
docker run -p 5000:5000 nlp-app
```

## Training and Testing

The project includes Jupyter notebooks for both training and testing:

- Training notebooks are located in the `src/notebooks/training/` directory
- Testing notebooks are available in the `src/notebooks/testing/` directory

## Deployment Architecture

The project uses a microservices architecture:
1. DeepSeek Service: Handles the core model inference with GPU support
2. NER Service: Provides the NER functionality and interfaces with the DeepSeek service

Both services are containerized and deployed to Google Cloud Run for scalability and reliability.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Contact

Your Name - Pisipati Sreekar Bharadwaj
