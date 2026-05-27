pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Restart Containers') {
            steps {
                sh 'docker compose down'
                sh 'docker compose up -d'
            }
        }

    }
}