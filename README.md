# My Java Web Application

A simple Java web application with CI/CD pipeline using GitHub Actions.

## CI/CD Pipeline

This repository includes a GitHub Actions workflow that automates the following steps:

1. **Build**: Compiles the Java code and packages it as a WAR file
2. **Test**: Runs unit tests to ensure code quality
3. **Docker**: Builds and pushes a Docker image to Docker Hub (when merged to main/master)
4. **Approval**: Requires manual approval before proceeding to deployment
5. **Deploy**: Deploys the application to the production environment

### Interactive Approval Process

The CI/CD pipeline includes an interactive approval process with the following features:

1. **Manual Approval**: Requires explicit approval from authorized team members before deployment
2. **Rejection with Comments**: If rejected, allows adding comments explaining the reason
3. **Resume Capability**: Ability to resume the deployment process after addressing concerns
4. **Approval History**: Maintains a record of approvals and rejections with comments

## Setup Requirements

To use the CI/CD pipeline, you need to set up the following:

### GitHub Secrets

1. `DOCKER_USERNAME`: Your Docker Hub username
2. `DOCKER_PASSWORD`: Your Docker Hub password or access token

### Environment for Approval Process

1. Create a GitHub environment named `production-approval`
2. Add required approvers to the environment protection rules

### Setting up secrets in GitHub

1. Go to your repository on GitHub
2. Click on "Settings" > "Secrets and variables" > "Actions"
3. Click on "New repository secret"
4. Add the required secrets

### Setting up the approval environment

1. Go to your repository on GitHub
2. Click on "Settings" > "Environments"
3. Click on "New environment"
4. Name it `production-approval`
5. Add required reviewers who can approve deployments
6. Optionally, add a wait timer if you want a delay before approvals can be made

## Manual Workflow Trigger

### Triggering the CI/CD Pipeline

You can manually trigger the CI/CD pipeline by:

1. Going to the "Actions" tab in your GitHub repository
2. Selecting the "Java CI/CD Pipeline" workflow
3. Clicking on "Run workflow"

### Approving or Rejecting Deployments

When a deployment is waiting for approval:

1. You'll receive a notification if you're a designated approver
2. Go to the running workflow in the Actions tab
3. Click on the "Review deployments" button
4. Approve or reject the deployment

### Resuming a Rejected Deployment

If a deployment was rejected and you want to resume it with comments:

1. Go to the "Actions" tab in your GitHub repository
2. Select the "Resume Deployment" workflow
3. Click on "Run workflow"
4. Enter the original workflow run ID
5. Add your comments explaining the changes made
6. Select "approved" to proceed with deployment or "rejected" to keep it on hold
7. Click "Run workflow"

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