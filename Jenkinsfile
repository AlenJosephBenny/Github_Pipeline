pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = "alenjbenny24deakin@gmail.com"
        DIRECTORY_PATH = "/path/to/your/code"
        TESTING_ENVIRONMENT = "Staging"
        PRODUCTION_ENVIRONMENT = "AlenJosephBenny"
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo "Build the code using Maven."
                    // Example build command
                    // sh 'mvn clean install'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Run unit tests using JUnit and integration tests using TestNG."
                    // Example test command
                    // sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo "Analyze the code using SonarQube."
                    // Example SonarQube command
                    // sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo "Perform a security scan using OWASP Dependency-Check."
                    // Example security scan command
                    // sh 'dependency-check.sh --project MyApp --scan /path/to/your/code'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploy the application to a staging environment using AWS CLI."
                    // Example deployment command
                    // sh 'aws deploy ...'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Run integration tests on the staging environment using Selenium and Postman."
                    // Example integration test command
                    // sh 'selenium-server -port 4444 &'
                    // sh 'newman run postman_collection.json'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploy the application to the production environment using AWS CLI."
                    // Example production deployment command
                    // sh 'aws deploy ...'
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline execution completed."
        }
        success {
            mail to: "${env.EMAIL_RECIPIENT}",
                subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                body: "The pipeline has completed successfully."
        }
        failure {
            script {
                def log = currentBuild.rawBuild.getLog(100).join('\n')
                mail to: "${env.EMAIL_RECIPIENT}",
                    subject: "Pipeline Failure: ${currentBuild.fullDisplayName}",
                    body: "The pipeline has failed. Please check the logs for details:\n\n${log}"
            }
        }
    }
}
