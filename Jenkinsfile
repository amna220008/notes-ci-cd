pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/amna220008/notes-ci-cd.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Pipeline is working correctly'
            }
        }
    }
}
