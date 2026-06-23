pipeline {
    agent any

    stages {

        stage('Login to Docker Hub') {
            steps {
                bat 'echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin'
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker push amna220008/notes-app:latest'
            }
        }

    }
}