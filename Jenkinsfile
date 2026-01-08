pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Deploy') {
            steps {
                sh '''
                docker compose down
                docker compose build
                docker compose up -d
                '''
            }
        }
    }
}
