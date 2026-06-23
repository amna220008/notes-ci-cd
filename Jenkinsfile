pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Stage') {
            steps {
                echo 'Building project...'
                sh 'mkdir -p build'
                sh 'echo "Build successful" > build/result.txt'
            }
        }

        stage('Test Stage') {
            steps {
                echo 'Running tests...'
                sh 'echo "All tests passed"'
            }
        }

        stage('Package Stage') {
            steps {
                echo 'Packaging application...'
                sh 'tar -czf app.tar.gz build/'
            }
        }

        stage('Deploy Stage') {
            steps {
                echo 'Deploying application...'
                sh 'echo "Deployment successful"'
            }
        }
    }

    post {
        success {
            echo 'PIPELINE SUCCESS ✔'
        }
        failure {
            echo 'PIPELINE FAILED ✖'
        }
    }
}