pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Using Maven to compile and package the code.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running unit tests and integration tests.'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Using tools such as SonarQube to analyze code quality.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Using tools like OWASP Dependency-Check to identify vulnerabilities.'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying to a staging server.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests on the staging environment.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying to a production server.'
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded!'
            emailext subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                      body: "The pipeline ${currentBuild.fullDisplayName} has succeeded.",
                      to: 'ebibennypyr@gmail.com',
                      attachLog: true
        }
        failure {
            echo 'Pipeline failed!'
            emailext subject: "Pipeline Failure: ${currentBuild.fullDisplayName}",
                      body: "The pipeline ${currentBuild.fullDisplayName} has failed. Please check logs.",
                      to: 'ebibennypyr@gmail.com',
                      attachLog: true
        }
    }
}
