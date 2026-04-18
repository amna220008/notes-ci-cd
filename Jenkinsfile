pipeline {
    agent any

    environment {
        IMAGE_NAME = "YOUR_DOCKERHUB_USERNAME/flutter-app"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/amna220008/notes-ci-cd.git'
            }
        }

        stage('Setup Flutter') {
            steps {
                sh '''
                    echo "Downloading Flutter..."
                    git clone https://github.com/flutter/flutter.git -b stable
                    export PATH="$PATH:$PWD/flutter/bin"
                    flutter doctor
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    export PATH="$PATH:$PWD/flutter/bin"
                    flutter pub get
                '''
            }
        }

        stage('Build Flutter Web') {
            steps {
                sh '''
                    export PATH="$PATH:$PWD/flutter/bin"
                    flutter build web
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                    docker build -t $IMAGE_NAME .
                '''
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh '''
                    docker login -u YOUR_DOCKER_USERNAME -p YOUR_DOCKER_PASSWORD
                    docker push $IMAGE_NAME
                '''
            }
        }
    }
}
