pipeline {
    agent any

    environment {
        COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo '📦 Cloning from GitHub...'
                git branch: 'main', url: 'https://github.com/YourUsername/YourRepo.git'
            }
        }

        stage('Build and Deploy with Docker Compose') {
            steps {
                echo '🚀 Deploying application using Docker Compose...'
                sh '''
                    docker compose down
                    docker compose build
                    docker compose up -d
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
