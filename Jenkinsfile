pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                url:  https://github.com/vipulitinfra/flask-docker-jenkins           }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flaskapp .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop flaskcontainer || true'
                sh 'docker rm flaskcontainer || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name flaskcontainer flaskapp'
            }
        }
    }
}
