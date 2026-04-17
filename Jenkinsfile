pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Aman9295/docker-fastapi-test.git'
            }
        }

        stage('Stop Old Containers') {
            steps {
                sh 'docker compose down || true'
            }
        }

        stage('Build and Start Containers') {
            steps {
                sh 'docker compose up -d --build'
            }
        }

        stage('Check Running Containers') {
            steps {
                sh 'docker ps'
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