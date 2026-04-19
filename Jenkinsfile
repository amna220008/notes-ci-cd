pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/amna220008/notes-ci-cd'
            }
        }

        stage('Flutter Build') {
            steps {
                sh 'flutter pub get'
                sh 'flutter build web'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t flutter-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f flutter-container || true
                docker run -d -p 3000:80 --name flutter-container flutter-app
                '''
            }
        }
    }
}
