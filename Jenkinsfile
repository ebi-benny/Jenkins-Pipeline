pipeline {
    agent any

    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo 'Stage 1: Build'
                }
        }

        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests'
            }
        }

        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis'
            }
        }

        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan'
            }
        }

        // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging'
            }
        }

        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging'
            }
        }

        // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production'
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
