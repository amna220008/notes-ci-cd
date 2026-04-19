pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/amna220008/notes-ci-cd'
            }
        }

        stage('Flutter Build (Docker)') {
            steps {
                sh '''
                docker run --rm -v $PWD:/app -w /app cirrusci/flutter:stable \
                flutter pub get

                docker run --rm -v $PWD:/app -w /app cirrusci/flutter:stable \
                flutter build web
                '''
            }
        }

        stage('Docker Info') {
            steps {
                echo "Now ready for Docker build"
            }
        }

    }
}
