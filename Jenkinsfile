pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t flask-docker-app .'
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running container...'
                sh '''
                    docker rm -f flask-app || true
                    docker run -d -p 5000:5000 --name flask-app flask-docker-app
                '''
            }
        }
    }
}
