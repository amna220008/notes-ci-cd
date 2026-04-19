pipeline {
    agent {
        docker {
            image 'cirrusci/flutter:latest'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/amna220008/notes-ci-cd'
            }
        }

        stage('Get Packages') {
            steps {
                sh 'flutter pub get'
            }
        }

        stage('Build Web') {
            steps {
                sh 'flutter build web'
            }
        }
    }
}
