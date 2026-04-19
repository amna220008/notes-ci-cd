pipeline {
    agent any

    stages {

        stage('Flutter Build') {
            steps {
                bat 'flutter pub get'
                bat 'flutter build web'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t flutter-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker rm -f flutter-container || exit 0
                docker run -d -p 3000:80 --name flutter-container flutter-app
                '''
            }
        }
    }
}
