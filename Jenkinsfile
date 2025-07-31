pipeline {
    agent any

    stages {
        stage('Cloning Git') {
            steps {
                git 'https://github.com/Devendar096/jenkins-demo.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 5000:5000 flask-app'
            }
        }
    }
}
