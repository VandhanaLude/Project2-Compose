# Project2-Compose
This repository contains a Docker Compose configuration for setting up Jenkins with Docker-in-Docker (DinD) support. It enables a continuous integration/continuous deployment (CI/CD) environment using Jenkins, allowing it to execute Docker commands in a secure and isolated manner.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) (version 20.10 or later)
- [Docker Compose](https://docs.docker.com/compose/install/) (version 1.27 or later)
- Nodejs for 
- NPM

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/Project2-Compose.git
   cd Project2-Compose
   ```

2. **Create Docker Network**:
   Before running the containers, create a Docker network:
   ```bash
   docker network create jenkins_network
   ```

3. **Start the Services**:
   Use Docker Compose to start Jenkins and Docker-in-Docker:
   ```bash
   docker-compose up -d
   ```

## Configuration

The `docker-compose.yml` file defines the following services:

- **dind**: 
  - Runs Docker-in-Docker to allow Jenkins to execute Docker commands.
  - Configured with necessary volumes and privileges.

- **jenkins**:
  - Runs the Jenkins CI server.
  - Exposes ports 8080 for web access and 50000 for agent connections.
  - Configured to connect to the Docker-in-Docker service.


## Usage

1. **Accessing Jenkins**:
   After starting the services, open your web browser and navigate to:
   ```
   http://localhost:8080
   ```
   Use the initial admin password to log in, which can be retrieved using:
   ```bash
   docker logs jenkins
   ```

2. **Install Required Plugins**:
   Once logged in, navigate to **Manage Jenkins** > **Manage Plugins** and install the following plugins:
   - Docker
   - Docker Pipeline
   - Git
