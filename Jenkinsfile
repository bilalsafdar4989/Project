pipeline {
    agent any

    environment {
        DEPLOY_PATH = "/opt/GreenX_DCS_Assesment_Tool-main"
    }

    stages {
        stage('Checkout from GitHub') {
            steps {
                sshagent(['github-credentials']) {
                    git branch: 'main', url: 'git@github.com:bilalsafdar4989/Project.git'
                }
            }
        }

        stage('Deploy using Docker Compose') {
            steps {
                sh '''
                cd ${WORKSPACE}
                echo "🚀 Starting deployment..."
                docker compose down || true
                docker compose build
                docker compose up -d
                echo "✅ Deployment completed!"
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build and deployment successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
