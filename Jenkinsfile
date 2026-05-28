pipeline {
    agent any

    environment {
        APP_SERVER = '3.83.234.2'
        APP_USER = 'ubuntu'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Baisalov24/getting-started-app.git'
            }
        }

        stage('Deploy') {
            steps {
                sshagent(['app-server-ssh']) {
                    sh '''
                        ssh -o StrictHostKeyChecking=no $APP_USER@$APP_SERVER "
                            cd /home/ubuntu &&
                            if [ ! -d getting-started-app ]; then
                                git clone https://github.com/Baisalov24/getting-started-app.git
                            fi &&
                            cd getting-started-app &&
                            git pull origin main &&
                            sudo docker compose up -d --build --remove-orphans
                        "
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}