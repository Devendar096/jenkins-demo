pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t flask-docker-app docker.'
            }
        }

        stage('Stop Existing Container') {
            steps {
                echo 'Stopping and removing old container if exists...'
                sh 'docker rm -f flask-app || true'
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running Docker container...'
                sh 'docker run -d -p 5000:5000 --name flask-app flask-docker-app'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'docker run --rm flask-docker-app python -m unittest test_app.py'
            }
        }

stage('Cloning Git') {
steps {
checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Devendar096', url: 'https://github.com/Devendar096/jenkins-demo-.git']])
}

    }
}
}
