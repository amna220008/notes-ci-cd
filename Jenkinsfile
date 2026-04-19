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
                sh '''
                flutter pub get
                flutter build web
                '''
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t notes-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f notes-container || true
                docker run -d -p 3000:80 --name notes-container notes-app
                '''
            }
        }
    }
}
