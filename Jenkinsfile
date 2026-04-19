pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/amna220008/notes-ci-cd'
            }
        }

        stage('Build Flutter') {
            steps {
                sh 'flutter pub get'
                sh 'flutter build web'
            }
        }

        stage('Docker Build') {
            steps {
                echo "Build Docker image here"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy step"
            }
        }
    }
}
