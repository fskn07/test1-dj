pipeline {
    agent any

    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh 'docker build -t application-($(git rev-parse --abbrev-ref HEAD).toLowerCase()):$BUILD_NUMBER . '
                }
            }    
        }
    }
}
