pipeline {
    agent any

    options {
        skipDefaultCheckout()
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo "Pulling code from GitHub"
                checkout scm
            }
        }

        stage('Verify Files') {
            steps {
                sh "ls -l"
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image"
                sh "docker build -t devops-frontend:ci ."
            }
        }

        stage('Verify Image') {
            steps {
                sh "docker images | grep devops-frontend"
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop frontend-test || true
                docker rm frontend-test || true
                docker run -d -p 8085:80 --name frontend-test devops-frontend:ci
                '''
            }
        }
    }
}
