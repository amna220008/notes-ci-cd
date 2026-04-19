pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/amna220008/notes-ci-cd'
            }
        }

        stage('Install Flutter (inside Jenkins container)') {
            steps {
                sh '''
                apt update
                apt install -y git curl unzip xz-utils

                git clone https://github.com/flutter/flutter.git -b stable
                export PATH="$PATH:`pwd`/flutter/bin"

                flutter --version
                flutter pub get
                '''
            }
        }

        stage('Build Web') {
            steps {
                sh '''
                export PATH="$PATH:`pwd`/flutter/bin"
                flutter build web
                '''
            }
        }

    }
}
