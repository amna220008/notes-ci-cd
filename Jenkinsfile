pipeline {
    agent any

    environment {
        IMAGE_NAME = "amna220008/notes-ci-cd"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/amna220008/notes-ci-cd.git'
            }
        }

        stage('Build App') {
            steps {
                sh 'mkdir -p build'
                sh 'echo "CI/CD SUCCESS" > build/index.html'
            }
        }

        stage('Create Dockerfile') {
            steps {
                writeFile file: 'Dockerfile', text: '''
                FROM nginx:alpine
                COPY build /usr/share/nginx/html
                '''
            }
        }

        stage('Build Docker Image (Shell)') {
            steps {
                sh 'docker build -t amna220008/notes-ci-cd:latest .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh '''
                echo "$DOCKER_PASS" | docker login -u amna220008 --password-stdin
                docker push amna220008/notes-ci-cd:latest
                '''
            }
        }
    }
}
