pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t password-generator:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker stop password-generator || true
                    docker rm password-generator || true
                    docker run -d --name password-generator password-generator:latest
                '''
            }
        }
    }
}