stage('Setup Flutter') {
    steps {
        sh '''
            echo "Cleaning old Flutter folder..."
            rm -rf flutter

            echo "Cloning Flutter..."
            git clone https://github.com/flutter/flutter.git -b stable
        '''
    }
}
