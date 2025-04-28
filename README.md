# My Java Web Application

A simple Java web application with CI/CD pipeline using GitHub Actions.

## CI/CD Pipeline

This repository includes a GitHub Actions workflow that automates the following steps:

1. **Build**: Compiles the Java code and packages it as a WAR file
2. **Test**: Runs unit tests to ensure code quality
3. **Docker**: Builds and pushes a Docker image to Docker Hub (when merged to main/master)
4. **Deploy**: Prepares for deployment (placeholder for actual deployment steps)

## Setup Requirements

To use the CI/CD pipeline, you need to set up the following secrets in your GitHub repository:

1. `DOCKER_USERNAME`: Your Docker Hub username
2. `DOCKER_PASSWORD`: Your Docker Hub password or access token

### Setting up secrets in GitHub

1. Go to your repository on GitHub
2. Click on "Settings" > "Secrets and variables" > "Actions"
3. Click on "New repository secret"
4. Add the required secrets

## Manual Workflow Trigger

You can manually trigger the workflow by:

1. Going to the "Actions" tab in your GitHub repository
2. Selecting the "Java CI/CD Pipeline" workflow
3. Clicking on "Run workflow"

## Local Development

### Prerequisites

- JDK 11 or higher
- Maven
- Docker (optional)

### Building the application

```bash
mvn clean package
```

### Running tests

```bash
mvn test
```

### Building Docker image locally

```bash
docker build -t my-app .
```

### Running the application locally

```bash
docker run -p 8080:8080 my-app
```

Then access the application at http://localhost:8080/myweb/