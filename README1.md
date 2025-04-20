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


Presetup
Required the Python installed (to run the blezemeter commands)
Required blizmeter setup (install the blazemeter torus which is python based)

Run the 

To run the JMeter GUI
C:\Users\vinitin\Downloads\apache-jmeter-5.6.3\apache-jmeter-5.6.3\bin\jmeter.bat

To run the app server (health application):
cd .\app\
node server.js

To run the tests:
cd .\performance-tests
bzt load_test.yml -o "modules.jmeter.properties.USERS=5" -o "modules.jmeter.properties.RAMP_UP=1"