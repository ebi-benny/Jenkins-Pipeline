pipeline {
    agent any

    stages {
        // Stage 1: Checkout
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                // Checkout code from Git repository
                checkout scm
            }
        }

        // Stage 2: Build
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Use a build automation tool such as Maven or Gradle
                sh 'mvn clean package' 
            }
        }

        // Stage 3: Test
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Run unit and integration tests
                sh 'mvn test' 
            }
        }

        // Stage 4: Deploy to Staging
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                // Deploy the application to a staging server
                sh 'deploy_to_staging.sh' 
            }
        }

        // Stage 5: Integration Tests on Staging
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Run integration tests on the staging environment
                sh 'integration_tests.sh' 
            }
        }

        // Stage 6: Deploy to Production
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // Deploy the application to a production server
                sh 'deploy_to_production.sh' 
            }
        }
    }

    // Post-build actions for notifications
    post {
        // Send email notification on success
        success {
            echo 'Pipeline completed successfully!'
            mail(
                to: 'ebibennypyr@gmail.com', 
                subject: 'Pipeline Success: Build ${env.BUILD_NUMBER}',
                body: 'The pipeline has completed successfully. Check Jenkins for more details.'
            )
        }

        // Send email notification on failure
        failure {
            echo 'Pipeline failed!'
            mail(
                to: 'ebibennypyr@gmail.com', 
                subject: 'Pipeline Failure: Build ${env.BUILD_NUMBER}',
                body: 'The pipeline has failed. Check Jenkins for more details.'
            )
        }
    }
}
