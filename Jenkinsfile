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

        stage('Install Flutter Dependencies') {
            steps {
                sh '''
                    echo "Installing Flutter dependencies..."
                    flutter pub get
                '''
            }
        }

        stage('Build Flutter Web') {
            steps {
                sh '''
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
