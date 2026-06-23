pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/amna220008/notes-ci-cd.git'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t amna220008/notes-app:latest .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push amna220008/notes-app:latest'
            }
        }
    }
}