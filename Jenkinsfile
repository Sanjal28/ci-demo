pipeline {
    agent any

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
    }
}
