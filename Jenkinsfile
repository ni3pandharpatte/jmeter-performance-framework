// Jenkinsfile
pipeline {
    agent any

    parameters {
        string(name: 'USERS', defaultValue: '10')
        string(name: 'RAMP_UP', defaultValue: '1m')
        string(name: 'ENVIRONMENT', defaultValue: 'dev')
    }

    environment {
        SLACK_WEBHOOK_URL = credentials('slack-webhook-url')
    }

    stages {
        stage('Install App Dependencies') {
            steps {
                sh 'npm install --prefix app'
            }
        }

        stage('Start Health App') {
            steps {
                script {
                    def proc = "node app/server.js &".execute()
                    sleep(5)
                }
            }
        }

        stage('Run JMeter (Taurus)') {
            steps {
                sh """
                cd performance-tests
                bzt load_test.yml -o execution.0.concurrency=${params.USERS} -o execution.0.ramp-up=${params.RAMP_UP}
                """
            }
        }

        stage('Notify Slack') {
            steps {
                sh """
                curl -X POST -H 'Content-type: application/json' --data '{"text":"Performance Test Completed: ENV=${params.ENVIRONMENT}, USERS=${params.USERS}"}' $SLACK_WEBHOOK_URL
                """
            }
        }
    }
}
