pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/RohitPatil18/docker-fastapi-test.git'
            }
        }

        stage('Stop Old Containers') {
            steps {
                bat 'docker compose down'
            }
        }

        stage('Build and Start Containers') {
            steps {
                bat 'docker compose up -d --build'
            }
        }

        stage('Check Running Containers') {
            steps {
                bat 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully. FastAPI app deployed with Docker Compose.'
        }
        failure {
            echo 'Pipeline failed. Please check console output.'
        }
    }
}