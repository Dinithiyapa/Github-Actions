# devops-challenge-apps
This repository contains code for a multi-tier application along with various workflows for building, testing, releasing, and deploying Docker images.

## The application overview:


```
web <=> api <=> db
```


## Branch Overview
### 1. main branch
In this branch, several workflows are defined to automate various tasks such as building, pushing Docker images, running tests, and releasing the application.

#### Workflow Files:

- **build-and-push-docker-images-parallel.yml**:
  This workflow builds and pushes Docker images for **Web** and **API** services in parallel, leveraging GitHub Actions to manage the CI/CD pipeline.

- **docker-build-and-push.yml**:
  This workflow handles building and pushing Docker images for the application.

- **release.yml**:
  This workflow automates the release process of the Docker images to Docker Hub or a repository, ensuring that the correct versions are tagged.

- **run-tests.yml**:
  This workflow runs tests to ensure the application is functioning as expected before proceeding with deployment.

- **scheduled-build.yml**:
  This workflow is scheduled to run periodically (e.g., nightly builds) to keep the images up-to-date or trigger maintenance tasks automatically.

---

### Workflow Details:

1. **To Trigger the Workflow**:
   - These workflows are triggered by specific actions:
     - **Push to main branch**: Workflows such as building, testing, and releasing will trigger automatically when pushing changes to the `main` branch.
     - **Scheduled Builds**: Some workflows are set to run periodically (e.g., nightly) as per the `scheduled-build.yml` file.
   
2. **To Deploy**:
   - Once the workflows are completed successfully (i.e., Docker images are built, tested, and released), the multi-tier application can be deployed using Docker Compose or Docker Swarm.

---

## Prerequisites
Before deploying the application, ensure the following tools are installed:

- **Docker**: [Install Docker](https://www.docker.com/get-started)
- **Docker Compose**: [Install Docker Compose](https://docs.docker.com/compose/install/)
- **Docker Swarm**: [Set up Docker Swarm](https://docs.docker.com/engine/swarm/)
- **Git**: [Install Git](https://git-scm.com/)
- **GitHub Account**: [Create a GitHub account](https://github.com/) (for triggering workflows)

---

## Deployment Details
The deployment configuration can be customized by modifying the `docker-compose.yml` file:

- **Ports**: Adjust the ports for both **Web** and **API** services in the `ports` section.
- **Scaling**: Change the number of instances for each service in the Docker Compose command or Docker Swarm setup.
- **Environment Variables**: Configure environment variables for **Web**, **API**, and **DB** services in the `docker-compose.yml` file.

---

## Accessing the Services
Once the services are up and running, you can access them:

- **Web Service**: Accessible via `http://web.example.com` (or the specified port).
- **API Service**: Accessible via `http://api.example.com` (or the specified port).

## Testing with `curl`

You can test the services using `curl`:

1. **Web Service**:
   ```bash
   curl http://web.example.com
   curl http://api.example.com

### Key Workflow Details:
- **build-and-push-docker-images-parallel.yml**: This is the workflow for building and pushing Docker images for both the Web and API services simultaneously, helping optimize the process.
- **docker-build-and-push.yml**: Handles building and pushing Docker images in a sequential manner.
- **release.yml**: Handles releasing Docker images after successful builds, ensuring that the correct versions are deployed.
- **run-tests.yml**: Executes the tests to ensure that the application works properly after changes.
- **scheduled-build.yml**: A cron-based workflow that runs periodically to keep images updated or trigger maintenance tasks.

This structure ensures smooth automation for building, testing, and releasing Docker images as part of the CI/CD pipeline.

