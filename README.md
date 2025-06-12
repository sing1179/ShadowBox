ShadowBox – AI-Powered Silent Cyberattack Simulation Tool
A Python-based tool to simulate cyberattacks in isolated Docker environments, analyze vulnerabilities using OpenAI, and log results to Google Cloud. Built with FastAPI for a modern, scalable API.
Features
Silent cyberattack simulation in Docker containers
AI-powered vulnerability analysis using OpenAI GPT
Google Cloud Logging integration for secure, scalable log storage
REST API with versioning and health checks
CI/CD ready (GitHub Actions example included)
Dockerized for easy deployment
Prerequisites
Python 3.8+
Docker (running locally)
OpenAI API key
Google Cloud Service Account JSON (for logging, optional)
Git
Installation
Clone the repository:
Apply to CyberSecurit...
Run
   git clone <your-repo-url>
   cd <your-repo-directory>
Install dependencies:
Apply to CyberSecurit...
Run
   pip install fastapi uvicorn docker openai google-cloud-logging python-dotenv
Set up environment variables:
Create a .env file in the project root with:
Apply to CyberSecurit...
   OPENAI_API_KEY=your_openai_api_key
   GOOGLE_APPLICATION_CREDENTIALS=path_to_your_gcp_service_account.json
   GCP_PROJECT_ID=your_gcp_project_id
Or export them in your shell.
Running the Application
Apply to CyberSecurit...
Run
uvicorn CyberSecurity:app --reload
The API will be available at http://localhost:8000.
API Endpoints
Health Check:
GET /api/v1/simulation/health
API Version:
GET /api/v1/simulation/version
Start Simulation:
POST /api/v1/simulation/start
Request Body Example:
Apply to CyberSecurit...
  {
    "environment_image": "python:3.10-slim",
    "attack_type": "privilege_escalation"
  }
Example Request
Apply to CyberSecurit...
Run
curl -X POST "http://localhost:8000/api/v1/simulation/start" \
  -H "Content-Type: application/json" \
  -d '{"environment_image": "python:3.10-slim", "attack_type": "privilege_escalation"}'
Docker Deployment
Dockerfile is included in the code (see comments). To build and run:
Apply to CyberSecurit...
Run
docker build -t shadowbox .
docker run -p 8000:8000 --env-file .env shadowbox
CI/CD
A sample GitHub Actions workflow is included in the code comments for automated build, test, and deployment to Google Cloud Run.
Notes
The attack simulation is mocked for safety. Extend simulate_attack for real scenarios.
Google Cloud Logging is optional; if not configured, logs print to console.
OpenAI API key is required for vulnerability analysis.
License
MIT License
Acknowledgements
FastAPI
Docker SDK for Python
OpenAI API
Google Cloud Logging
