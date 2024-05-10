pipeline {
    agent any

    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Using Maven to compile and package the code.'
                }
        }

        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running unit tests and integration tests.'
            }
        }

        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Using tools such as SonarQube to analyze code quality.'
            }
        }

        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Using tools like OWASP Dependency-Check to identify vulnerabilities.'
            }
        }

        // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying to a staging server.'
            }
        }

        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests on the staging environment.'
            }
        }

        // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying to a production server.'
            }
        }
    }

    // Post-build actions for notifications
    post {
        success {
            echo 'Pipeline succeeded!'
            mail to: 'ebibennypyr@gmail.com',
                 subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                 body: "The pipeline ${currentBuild.fullDisplayName} has succeeded."
        }
        failure {
            echo 'Pipeline failed!'
            mail to: 'ebibennypyr@gmail.com',
                 subject: "Pipeline Failure: ${currentBuild.fullDisplayName}",
                 body: "The pipeline ${currentBuild.fullDisplayName} has failed. Please check logs."
        }
    }
}

