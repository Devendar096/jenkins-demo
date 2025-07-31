pipeline {
    agent any

    stages {
        stage('Cloning Git') {
            steps {
                git url: 'https://github.com/Devendar096/jenkins-demo.git', branch: 'main'

            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }


        stage('Cleanup Existing Containers') {
    steps {
        sh '''
        if docker ps -q --filter "ancestor=flask-app" | grep .; then
          docker rm -f $(docker ps -q --filter "ancestor=flask-app")
        fi
        '''
    }
}


        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 5050:5000 flask-app'
            }
        }
    }
}
