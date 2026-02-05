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
                echo "Listing files in workspace"
                sh "ls -l"
            }
        }

        stage('Read File') {
            steps {
                echo "Displaying index.html content"
                sh "cat index.html"
            }
        }
    }
}
