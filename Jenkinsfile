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
                sh 'echo "CI/CD SUCCESS - Flutter/Web build simulated" > build/index.html'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    writeFile file: 'Dockerfile', text: '''
                    FROM nginx:alpine
                    COPY build /usr/share/nginx/html
                    '''
                    dockerImage = docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        dockerImage.push("latest")
                    }
                }
            }
        }
    }
}
