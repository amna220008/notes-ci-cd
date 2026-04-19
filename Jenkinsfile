stage('Login to Docker Hub') {
    steps {
        sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
    }
}

stage('Push Image') {
    steps {
        sh 'docker push amna220008/notes-app:latest'
    }
}
