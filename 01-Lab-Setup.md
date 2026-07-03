# 01 - Lab Setup

## 🎯 Objective

The objective of this phase was to establish a secure and reproducible penetration testing laboratory using OWASP Juice Shop. This involved deploying the application locally with Docker, verifying that the environment functioned correctly, and preparing the tools required for subsequent security testing.
The lab environment was designed to simulate a real-world web application assessment while ensuring that all testing was performed within an isolated and authorized environment.

## 🖥️ Lab Environment

The penetration testing environment was configured using the following software and tools.

| Component | Configuration |
|-----------|---------------|
| Host Operating System | Kali Linux |
| Target Application | OWASP Juice Shop |
| Deployment Method | Docker Container |
| Proxy Tool | Burp Suite Community Edition |
| Web Browser | Burp Embedded Browser |
| Reconnaissance Tools | Nmap, Gobuster, cURL |
| Testing Environment | Localhost (127.0.0.1) |

## 🚀 Deployment Preparation

Before deploying the target application, Docker was used to provide an isolated and reproducible environment for running OWASP Juice Shop.

The deployment process included verifying that Docker was installed correctly, confirming that the Docker service was running, and testing the installation by executing a sample container before deploying the target application.

This approach ensured that the testing environment was stable and minimized configuration issues during the penetration testing process.

## ✅ Docker Installation Verification

The first step was to verify that Docker was installed correctly on the host operating system before attempting to deploy the target application.

Docker version information was checked from the terminal to ensure that the Docker CLI was available and functioning correctly.

### Verification Command

```bash
docker --version
```

### Purpose

- Verify that Docker is installed.
- Confirm that the Docker CLI is accessible from the terminal.
- Ensure the environment is ready for container deployment.


## 🐳 Docker Functionality Test

Before deploying the target application, Docker functionality was verified by running the official **Hello World** container.

This step confirmed that the Docker daemon was running correctly, container images could be downloaded from Docker Hub, and containers could execute successfully.

### Test Command

```bash
docker run hello-world
```

### Purpose

- Verify communication with the Docker daemon.
- Confirm successful image download from Docker Hub.
- Ensure containers can start and execute correctly.
- Validate that the Docker environment is fully operational before deploying the target application.

### Expected Outcome

The container displays a welcome message indicating that Docker is installed correctly and functioning as expected.

## 📦 Deploying OWASP Juice Shop

After confirming that Docker was functioning correctly, the OWASP Juice Shop application was deployed as a Docker container.

The container was configured to expose the application on port **3000**, allowing it to be accessed locally through a web browser.

### Deployment Command

```bash
docker run -d --name juice-shop -p 3000:3000 bkimminich/juice-shop
```

### Command Explanation

| Option | Description |
|---------|-------------|
| `-d` | Runs the container in detached mode (background). |
| `--name juice-shop` | Assigns the container the name **juice-shop**. |
| `-p 3000:3000` | Maps port 3000 of the host machine to port 3000 inside the container. |
| `bkimminich/juice-shop` | Official Docker image of OWASP Juice Shop. |

### Purpose

- Deploy the target application in an isolated environment.
- Expose the web application on the local machine.
- Prepare the application for penetration testing.

## ✅ Container Verification

After deploying the OWASP Juice Shop container, its status was verified to ensure that the application was running correctly.

### Verification Command

```bash
docker ps
```

### Purpose

- Verify that the **juice-shop** container is running.
- Confirm that the Docker container has started successfully.
- Check the mapped network ports.
- Ensure the application is ready for web access.

### Expected Output

The running container should appear in the list with a status similar to:

```text
CONTAINER ID   IMAGE                   STATUS      PORTS
xxxxxxxxxxxx   bkimminich/juice-shop   Up ...      0.0.0.0:3000->3000/tcp
```

The **STATUS** column should indicate that the container is **Up**, confirming that the application is running successfully.


## 🌐 Application Access Verification

After confirming that the Docker container was running successfully, the OWASP Juice Shop application was accessed through a web browser.

### Application URL

```text
http://localhost:3000
```

### Verification Process

The application homepage was loaded using the Burp Embedded Browser to verify that:

- The web application was accessible.
- The HTTP service was responding correctly.
- Burp Suite was able to intercept application traffic.
- The penetration testing environment was fully operational.

### Expected Outcome

The OWASP Juice Shop landing page should load successfully, indicating that the deployment was successful and the application is ready for security testing.

## 🔧 Troubleshooting and Resolutions
### Issue 1: Docker Container Stopped Unexpectedly

#### Problem

During the penetration testing lab, the OWASP Juice Shop Docker container occasionally stopped running unexpectedly. As a result, the application became inaccessible through the browser.

#### Diagnosis

The container status was verified using:

```bash
docker ps
docker ps -a
```

These commands confirmed whether the container was actively running or had exited.

#### Resolution

The container was restarted using:

```bash
docker start juice-shop
```

If necessary, the container was removed and redeployed to restore the testing environment.

#### Outcome

The application became accessible again through:

```text
http://localhost:3000
```

allowing penetration testing activities to continue successfully.

### Issue 2: "Blocked Illegal Activity" Error

#### Problem

While accessing profile-related pages such as **My Addresses**, the application displayed the following error:

```text
500 Error: Blocked illegal activity by ::ffff:172.17.0.1
```

The error prevented further interaction with the affected functionality.

#### Diagnosis

The application logs were inspected using:

```bash
docker logs juice-shop --tail 50
```

The logs confirmed that the application was still running and recorded the following message:

```text
Error: Blocked illegal activity by ::ffff:172.17.0.1
```

Additional testing revealed that the issue was not caused by Docker or Burp Suite itself.

#### Root Cause

The Burp Embedded Browser retained authentication cookies and local storage from a previous Juice Shop instance. After recreating the Docker container, the browser continued sending outdated session information, resulting in inconsistent application behavior.

#### Resolution

The issue was resolved by:

- Clearing browser cookies and cached site data.
- Opening a fresh Burp Embedded Browser session.
- Registering a new test account.
- Logging in again using the new session.

#### Outcome

After clearing the browser state, the application functioned normally and penetration testing activities resumed successfully.



## ✅ Lab Setup Summary

The laboratory environment was successfully configured using Docker and OWASP Juice Shop. All required tools were verified before beginning the penetration testing assessment.

During the setup process, multiple environment-related issues were encountered and systematically resolved through troubleshooting and verification. This ensured that the testing environment remained stable, reproducible, and suitable for conducting web application security assessments.

With the lab fully operational, the assessment proceeded to the reconnaissance and enumeration phase.
