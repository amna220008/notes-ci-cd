pipeline {
    agent any

    environment {
        IMAGE_NAME = "yourdockerhubusername/flutter-app"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/your-repo-url.git'
            }
        }

        stage('Install Flutter Dependencies') {
            steps {
                sh 'flutter pub get'
            }
        }

        stage('Build Flutter Web') {
            steps {
                sh 'flutter build web'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-credentials-id') {
                        dockerImage.push("latest")
                    }
                }
            }
        }
    }
}
