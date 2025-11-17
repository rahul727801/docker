pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/rahul727801/docker.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t simple-webapp .'
            }
        }

        stage('Test') {
            steps {
                sh 'pip3 install -r requirements.txt'
                sh 'pytest -q'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop simple-webapp || true'
                sh 'docker rm simple-webapp || true'
                sh 'docker run -d -p 8000:8000 --name simple-webapp simple-webapp'
            }
        }
    }
}

