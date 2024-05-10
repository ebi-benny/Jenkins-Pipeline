pipeline {
    agent any

    triggers {
        // Trigger pipeline on new commits
        githubPush()
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Use a build automation tool like Maven to build the code
                    sh 'mvn clean package'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Run unit tests and integration tests (e.g., using JUnit)
                    sh 'mvn test'
                }
            }
            post {
                always {
                    // Send email notification for test stage
                    emailext body: 'Test stage completed with ${currentBuild.currentResult}',
                            subject: 'Jenkins Pipeline - Test Stage',
                            to: 'ebibennypyr@gmail.com'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    // Use a code analysis tool like SonarQube
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    // Use a security scan tool like OWASP ZAP
                    sh 'zap-baseline.py -t http://yourapp.com'
                }
            }
            post {
                always {
                    // Send email notification for security scan stage
                    emailext body: 'Security scan completed with ${currentBuild.currentResult}',
                            subject: 'Jenkins Pipeline - Security Scan',
                            to: 'ebibennypyr@gmail.com'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    // Deploy to a staging server (e.g., AWS EC2 instance)
                    sh 'aws deploy ...'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    // Run integration tests on staging (e.g., using Selenium)
                    sh 'mvn verify'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    // Deploy to a production server (e.g., AWS EC2 instance)
                    sh 'aws deploy ...'
                }
            }
        }
    }
}
