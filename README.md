# 🧪 JMeter Performance Testing Framework

This project offers a **comprehensive performance testing solution** leveraging:

- **Node.js**: A basic health check API serving as the test target.
- **Apache JMeter**: Used for crafting and executing performance tests.
- **Taurus (bzt)**: A YAML-driven test runner for JMeter scripts.
- **BlazeMeter**: An optional cloud platform for test execution and reporting.
- **Gradle**: For automating the execution of performance tests.
- **Jenkins**: Enables CI/CD integration with parameterized test execution and Slack notifications.

---

## 🚀 Getting Started

### 1️⃣ Launch the Sample Node.js Application

```bash
cd app
npm install
node server.js
This command will start the Node.js server, making the health check endpoint accessible at http://localhost:8080/health.

2️⃣ Execute JMeter Tests with Taurus
Ensure you have Python installed. Then, install Taurus:

Bash

pip install bzt
Navigate to the performance tests directory and run your test:

Bash

cd performance-tests
bzt load_test.yml -o "modules.jmeter.properties.USERS=5" -o "modules.jmeter.properties.RAMP_UP=1"
3️⃣ Run Performance Tests using Gradle
Bash

./gradlew runPerformanceTest
This command will trigger Taurus using the configurations specified in the build.gradle file.

4️⃣ Integrate with Jenkins (CI/CD)
Utilize the provided Jenkinsfile to seamlessly integrate this framework into your Jenkins pipeline. It offers:

Automatic triggering upon code pushes to develop or master branches.
Slack notifications for test results.
Parameterized test execution, allowing you to configure:
USERS: The number of concurrent users.
RAMP_UP: The duration (in seconds) to ramp up the users.
ENVIRONMENT: The target environment (dev, qa, prod).
Configure these parameters within your Jenkins job.

5️⃣ Configure Slack Notifications
To receive test result updates on Slack:

Add a Jenkins credential named slack-webhook-url containing your Slack webhook URL.
The Jenkinsfile includes a stage that uses this credential to send notifications.
📁 Project Structure
Bash

project-root/
├── app/                    # Node.js health check application
│   └── server.js
├── performance-tests/      # JMeter scripts & Taurus configurations
│   ├── load_test.yml
│   └── health_api_test.jmx
├── Jenkinsfile             # Jenkins CI pipeline configuration
├── build.gradle            # Gradle script for test execution
├── .gitignore
└── README.md               # This guide
⚙️ Prerequisites
Python: Necessary for running Taurus and BlazeMeter.
Node.js: Required to execute the sample application.
Apache JMeter: Optional GUI for viewing and editing .jmx files.
Taurus: Install using pip install bzt.
📌 Optional - JMeter GUI
To run JMeter in GUI mode:

Bash

# Example path - adjust based on your system
/Applications/ApacheJMeter.app/Contents/Resources/bin/jmeter.sh # For macOS
C:\apache-jmeter-5.6.3\bin\jmeter.bat                       # For Windows
Use this to open and inspect the performance-tests/health_api_test.jmx file.

✅ Health Check Endpoint
Verify the sample application is running correctly by sending a request to the health check endpoint:

Bash

curl http://localhost:8080/health
Expected response:

JSON

{ "status": "UP" }
Happy performance testing!