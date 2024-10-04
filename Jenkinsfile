pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'archit7787@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the code using Mavenn'
                    // Example: sh 'mvn clean package'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests'
                    // Example: sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Running code analysis using SonarQube'
                    // Example: sh 'sonar-scanner'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Running security scan using OWASP Dependency Check'
                    // Example: sh 'dependency-check --project myapp --scan .'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging environment'
                    // Example: sh 'scp target/myapp.war user@staging-server:/path/to/deploy'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging environment'
                    // Example: sh 'curl http://staging-server/api/test'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production environment'
                    // Example: sh 'scp target/myapp.war user@production-server:/path/to/deploy'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
        }
        success {
            echo 'Sending success notification email'
            emailext(
                to: "${EMAIL_RECIPIENT}",
                subject: "Pipeline Succeeded",
                body: "The pipeline has successfully completed all stages.",
                attachLog: true
            )
        }
        failure {
            echo 'Sending failure notification email'
            emailext(
                to: "${EMAIL_RECIPIENT}",
                subject: "Pipeline Failed",
                body: "The pipeline has failed. Please check the logs for details.",
                attachLog: true
            )
        }
    }
}
