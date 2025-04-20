# JMeter Performance Testing Framework

This project provides a complete performance testing framework using:

- **Node.js**: A sample health check API to test.
- **Apache JMeter**: Performance test scripts.
- **Taurus (bzt)**: Run JMeter tests easily with YAML configs.
- **BlazeMeter**: Optional cloud reporting.
- **Gradle**: Task runner for integration.
- **Jenkins**: CI/CD pipeline with Slack notifications.

## 🚀 Quick Start

### 1. Run the Node.js App

```bash
cd app
npm install
node server.js
```

### 2. Run JMeter test with Taurus

```bash
pip install bzt
bzt performance-tests/load_test.yml
```

### 3. Run via Gradle

```bash
./gradlew runPerformanceTest
```

### 4. Jenkins Pipeline

Use the included `Jenkinsfile` to trigger tests on push to `develop` or `master` branches. Set parameters like:

- `USERS`: number of concurrent users
- `RAMP_UP`: ramp-up time
- `ENVIRONMENT`: target environment (dev/qa/prod)

### 5. Slack Notification

Add your Slack webhook to Jenkins credentials (`slack-webhook-url`) to receive test reports.

---

## 📁 Project Structure

```
project-root/
├── app/                      # Sample Node.js application
├── performance-tests/        # JMeter test scripts and Taurus config
├── Jenkinsfile               # CI pipeline definition
├── build.gradle              # Gradle task for performance test
└── README.md
```
