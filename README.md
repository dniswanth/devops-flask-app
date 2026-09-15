# DevOps Flask Application

A simple Flask application containerized with Docker and automated using GitHub Actions CI/CD.

## Technologies Used

- Python
- Flask
- Pytest
- Gunicorn
- Docker
- GitHub Actions
- Docker Hub
- AWS EC2
- Git

## Project Structure

```text
devops-flask-app/
├── .github/
│   └── workflows/
│       └── ci.yml
├── tests/
│   └── test_app.py
├── app.py
├── Dockerfile
├── .dockerignore
├── .gitignore
├── requirements.txt
└── README.md
```

## Run Locally

Create and activate a virtual environment:

```bash
python -m venv venv
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
python app.py
```

Open the application in your browser:

```text
http://localhost:5000
```

## Run Tests

Run the test suite using Pytest:

```bash
python -m pytest
```

## Run with Docker

Build the Docker image:

```bash
docker build -t devops-flask-app .
```

Run the Docker container:

```bash
docker run -d -p 5000:5000 --name devops-flask-container devops-flask-app
```

Open the application:

```text
http://localhost:5000
```

To check the running container:

```bash
docker ps
```

To view container logs:

```bash
docker logs devops-flask-container
```

The application runs using Gunicorn as the production WSGI server.

## CI/CD Pipeline

GitHub Actions automatically performs the following steps whenever code is pushed to the `main` branch:

1. Checks out the source code
2. Sets up Python
3. Installs project dependencies
4. Runs the Pytest test suite
5. Builds the Docker image
6. Pushes the Docker image to Docker Hub
7. Connects to AWS EC2 using SSH
8. Pulls the latest Docker image
9. Stops and removes the previous container
10. Runs the latest container on the EC2 instance

The CI/CD workflow is defined in:

```text
.github/workflows/ci.yml
```

## Docker Hub

The Docker image is available on Docker Hub:

```text
niswanth13/devops-flask-app:latest
```

The image can be pulled using:

```bash
docker pull niswanth13/devops-flask-app:latest
```

## AWS EC2 Deployment

The Dockerized Flask application is deployed on an AWS EC2 instance.

The EC2 instance runs the Docker container and serves the Flask application using Gunicorn.

GitHub Actions automatically deploys the latest Docker image to the EC2 instance whenever changes are pushed to the `main` branch.

The application is accessible through:

```text
http://13.50.5.152
```

## Verification

The application was successfully tested locally using Pytest.

The Docker image was successfully built and run locally.

The Docker image was successfully pushed to Docker Hub.

The application was successfully deployed to AWS EC2.

GitHub Actions successfully runs the test suite, builds the Docker image, pushes the image to Docker Hub, and deploys the latest image to AWS EC2.

The deployed application displays:

```text
Hello, DevOps! CI/CD Deployment Successful!
```

## Project Workflow

```text
Code
  ↓
Git
  ↓
GitHub
  ↓
GitHub Actions
  ↓
Run Tests
  ↓
Build Docker Image
  ↓
Push Image to Docker Hub
  ↓
Deploy to AWS EC2
  ↓
Run Docker Container
  ↓
Gunicorn
  ↓
Flask Application
```
