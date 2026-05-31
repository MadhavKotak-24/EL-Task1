# CI/CD Pipeline Automation using GitHub Actions, Docker, and Node.js

## Project Overview

This project demonstrates a complete Continuous Integration (CI) pipeline using GitHub Actions. The pipeline automatically builds, tests, containerizes, and pushes a Node.js web application to DockerHub whenever code is pushed to the `main` branch.

The objective of this project is to automate the software delivery process and understand how modern DevOps workflows are implemented using GitHub Actions and Docker.

---

## Technologies Used

* Node.js
* Express.js
* Docker
* DockerHub
* Git
* GitHub
* GitHub Actions

---

## Project Architecture

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
GitHub Actions Workflow
    │
    ├── Checkout Source Code
    ├── Install Dependencies
    ├── Run Tests
    ├── Build Docker Image
    ├── Login to DockerHub
    └── Push Docker Image
                │
                ▼
            DockerHub
```

---

## Project Structure

```text
nodejs-demo-app/
│
├── .github/
│   └── workflows/
│       └── main.yml
│
├── app.js
├── package.json
├── Dockerfile
├── .gitignore
└── README.md
```

---

## Application Description

A simple Express.js application was created to demonstrate the CI/CD process.

When the application is accessed through a browser, it displays:

```text
CI/CD Pipeline Working
```

---

## Docker Configuration

A Dockerfile was created to containerize the Node.js application.

### Docker Workflow

1. Pull Node.js base image.
2. Create application working directory.
3. Copy package files.
4. Install dependencies.
5. Copy application source code.
6. Expose application port.
7. Start the application.

---

## GitHub Actions Workflow

The workflow is defined in:

```text
.github/workflows/main.yml
```

### Trigger

The workflow runs automatically when code is pushed to the `main` branch.

```yaml
on:
  push:
    branches:
      - main
```

### Workflow Stages

#### 1. Checkout Repository

Downloads the latest source code from GitHub.

#### 2. Setup Node.js

Installs the required Node.js runtime on the GitHub runner.

#### 3. Install Dependencies

Installs project dependencies using npm.

#### 4. Run Tests

Executes the application's test script.

#### 5. Login to DockerHub

Authenticates with DockerHub using GitHub Secrets.

#### 6. Build Docker Image

Builds a Docker image from the Dockerfile.

#### 7. Push Docker Image

Pushes the generated image to DockerHub.

---

## GitHub Secrets Used

To securely authenticate with DockerHub, the following GitHub repository secrets were configured:

| Secret Name     | Description            |
| --------------- | ---------------------- |
| DOCKER_USERNAME | DockerHub Username     |
| DOCKER_PASSWORD | DockerHub Access Token |

These secrets prevent sensitive credentials from being stored directly in the workflow file.

---

## Implementation Steps

### Step 1: Create Node.js Application

* Create `app.js`
* Create `package.json`
* Install Express.js

### Step 2: Create Dockerfile

* Define Node.js base image
* Configure application container
* Build container image

### Step 3: Create DockerHub Repository

* Create a DockerHub account
* Create a repository named `nodejs-demo-app`
* Generate a Docker Access Token

### Step 4: Create GitHub Repository

* Initialize Git repository
* Push project code to GitHub

### Step 5: Configure GitHub Secrets

Add:

* DOCKER_USERNAME
* DOCKER_PASSWORD

under:

```text
Repository Settings
→ Secrets and Variables
→ Actions
```

### Step 6: Create GitHub Actions Workflow

Create:

```text
.github/workflows/main.yml
```

Define all CI stages:

* Checkout
* Install
* Test
* Build
* Push

### Step 7: Push Code

Whenever code is pushed to the `main` branch:

```bash
git add .
git commit -m "Update application"
git push origin main
```

the workflow starts automatically.

### Step 8: Verify Pipeline Execution

Navigate to:

```text
GitHub Repository
→ Actions
```

Verify all workflow stages complete successfully.

### Step 9: Verify DockerHub Image

Navigate to DockerHub and confirm the image has been pushed successfully.

---

## CI/CD Workflow Execution Example

```text
Code Push
    │
    ▼
GitHub Actions Triggered
    │
    ▼
Checkout Repository
    │
    ▼
Install Dependencies
    │
    ▼
Run Tests
    │
    ▼
Docker Login
    │
    ▼
Build Docker Image
    │
    ▼
Push Image to DockerHub
    │
    ▼
Pipeline Completed Successfully
```

---

## Learning Outcomes

Through this project, the following concepts were learned:

* Continuous Integration (CI)
* GitHub Actions Workflow Automation
* Docker Containerization
* DockerHub Image Registry
* Secure Secret Management
* Automated Build Pipelines
* Source Control Integration
* DevOps Best Practices

---

## Future Enhancements

Possible improvements include:

* Automatic deployment to AWS EC2
* Multi-stage Docker builds
* Security scanning with Trivy
* Infrastructure as Code using Terraform
* Automated rollback strategy
* Slack/Email deployment notifications
* Kubernetes deployment automation

---

## Conclusion

This project successfully implements an automated CI pipeline using GitHub Actions. Every push to the `main` branch automatically triggers testing, Docker image creation, and image publishing to DockerHub, reducing manual effort and ensuring a consistent build process.
