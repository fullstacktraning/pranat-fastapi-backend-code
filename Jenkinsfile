pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/fullstacktraning/pranat-fastapi-backend-code.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fastapi-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop fastapi-container || true'
                sh 'docker rm fastapi-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8000:8000 --env-file /home/ubuntu/fastapi/.env --name fastapi-container fastapi-app'
            }
        }

    }
}