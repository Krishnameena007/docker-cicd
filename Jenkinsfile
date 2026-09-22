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
                sh 'docker build -t docker-cicd:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f docker-cicd || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name docker-cicd -p 8081:80 docker-cicd:v1'
            }
        }
    }
}
