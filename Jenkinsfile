pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the source code from the GitHub repository
                checkout scm
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                script {
                    // Deploy the application using docker-compose and compose.yml
                    sh 'docker compose -f compose.yml up -d --build'
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    // Verify running containers
                    sh 'docker ps'
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment succeeded!'
        }
        failure {
            echo 'Deployment failed!'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}
