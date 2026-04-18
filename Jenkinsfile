pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/amna220008/notes-ci-cd.git'
            }
        }

        stage('Build App') {
            steps {
                sh '''
                echo "Building application..."
                mkdir -p build
                echo "CI/CD SUCCESS - build completed"
                '''
            }
        }

        stage('Docker Step') {
            steps {
                echo "Simulating Docker build (no real Docker required)"
            }
        }

        stage('Push') {
            steps {
                echo "Simulating Docker push to Docker Hub"
            }
        }
    }
}
