pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                bat 'node --check app.js'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t node-rest-api .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat '''
                docker run -d -p 8090:3000 --name node-rest-api-container node-rest-api
                '''
            }
        }
    }
}