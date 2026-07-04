pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t corporate-website .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker stop corporate-website-container || exit /b 0'
                bat 'docker rm corporate-website-container || exit /b 0'
                bat 'docker run -d --name corporate-website-container -p 8080:80 corporate-website'
            }
        }
    }
}