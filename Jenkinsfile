pipeline {
    agent any

    stages {
        stage('Deploy Application') {
            steps {
                sh 'docker compose up -d --build --remove-orphans'
            }
        }
    }
}