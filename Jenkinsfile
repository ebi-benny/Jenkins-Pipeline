pipeline {
    agent any

    environment {
        CODE_DIRECTORY = "/path/to/code"
        TEST_ENV = "testing"
        PROD_ENV = "yourname_production"
        NOTIFICATION_EMAIL = "ebibennypyr@gmail.com"
    }

    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo "Fetching the source code from: $CODE_DIRECTORY"
                echo "Compiling the code and generating artifacts"
            }
        }
        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
            post {
                success {
                     // Send email notification if tests pass
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Unit and Integration Tests Passed",
                         body: "Unit and Integration Tests have passed successfully. See attached logs for details.<br>Console Output: ${env.BUILD_URL}console",
                         mimeType: 'text/html'
                }
                failure {
                    // Send email notification if tests fail
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Unit and Integration Tests Failed",
                         body: "Unit and Integration Tests have failed. See attached logs for details.<br>Console Output: ${env.BUILD_URL}console",
                         mimeType: 'text/html'
                }
            }
        }
        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo 'Checking the quality of the code'
            }
        }
         // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo 'Performing security scan'
            }
            post {
                success {
                    // Send email notification if security scan passes
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Security Scan Passed",
                         body: "Security scan completed without any issues. See attached logs for details.<br>Console Output: ${env.BUILD_URL}console",
                         mimeType: 'text/html'
                }
                failure {
                    // Send email notification if security scan fails
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Security Scan Failed",
                         body: "Security scan has some issues. See attached logs for details.<br>Console Output: ${env.BUILD_URL}console",
                         mimeType: 'text/html'
                }
            }
        }
         // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to the $TEST_ENV environment"
            }
        }
        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging environment"
            }
        }
         // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the $PROD_ENV environment"
            }
        }
    }

    // Post-build actions for notifications
    post {
        always {
            emailext (
                subject: "Pipeline Status: ${currentBuild.result}",
                body: '''<html>
                    <body>
                    <p>Build Status: ${currentBuild.result}</p>
                    <p>Build Number: ${currentBuild.number}</p>
                    <p>Console Output: <a href="${env.BUILD_URL}console">${env.BUILD_URL}console</a></p>
                    </body>
                    </html>''',
                to: 'ebibennypyr@gmail.com',
                from: 'jenkins@example.com',
                replyTo: 'jenkins@example.com',
                mimeType: 'text/html'
            )
        }
    }
}