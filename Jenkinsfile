pipeline {
    agent any

    environment {
        DEPLOY_PATH = "/opt/GreenX_DCS_Assesment_Tool-main"
    }

    stages {
        stage('Clone Repository') {
            steps {
                sshagent(['github-ssh']) {
                    git branch: 'main', url: 'git@github.com:bilalsafdar4989/Project.git'
                }
            }
        }

        stage('Build and Deploy using Docker Compose') {
            steps {
                sh '''
                cd ${WORKSPACE}
                docker compose down || true
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
