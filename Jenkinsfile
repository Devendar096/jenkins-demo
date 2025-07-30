pipeline {
    agent any

    stages {
        stage('Cloning Git') {
            steps {
                git branch: 'main', url: 'https://github.com/Devendar096/jenkins-demo.git'

            }
        }

        stage('Test Docker Access') {
            steps {
                 sh 'docker version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-docker-app .'
            }
        }

        stage('Stop and Remove Old Container') {
            steps {
                sh '''
                    docker stop flask-app || true
                    docker rm flask-app || true
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name flask-app flask-docker-app'
            }
        }
    }
}
