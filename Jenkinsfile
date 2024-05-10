pipeline {
    agent any
    environment {
        EMAIL_RECIPIENTS = 'ebibennypyr@gmail.com' 
    }

    // Define stages in the pipeline
    stages {
        // Stage 1: Build
        stage('Build') {
            steps {
                echo 'Building the code...'
                // Use a build automation tool such as Maven
                sh 'mvn clean install'
            }
        }

        // Stage 2: Unit and Integration Tests
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Run tests with a test automation tool
                sh 'mvn test'
            }
        }

        // Stage 3: Code Analysis
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                // Use a code analysis tool such as SonarQube
                sh 'sonar-scanner'
            }
        }

        // Stage 4: Security Scan
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Use a security scan tool such as Snyk
                sh 'snyk test'
            }
        }

        // Stage 5: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Deploy the application to a staging server 
                sh 'deploy-staging.sh'
            }
        }

        // Stage 6: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
                // Run integration tests in the staging environment
                sh 'run-integration-tests.sh'
            }
        }

        // Stage 7: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                // Deploy the application to a production server 
                sh 'deploy-production.sh'
            }
        }
    }

    // Post-build actions for notifications
    post {
        // Notify on successful pipeline completion
        success {
            echo 'Pipeline completed successfully!'
            mail(
                to: EMAIL_RECIPIENTS,
                subject: "Jenkins Pipeline Success - ${env.JOB_NAME}",
                body: "The Jenkins pipeline for ${env.JOB_NAME} completed successfully."
            )
        }

        // Notify on pipeline failure
        failure {
            echo 'Pipeline failed!'
            mail(
                to: EMAIL_RECIPIENTS,
                subject: "Jenkins Pipeline Failure - ${env.JOB_NAME}",
                body: "The Jenkins pipeline for ${env.JOB_NAME} failed. Please check the logs for details."
            )
        }
    }
}
