pipeline {
    agent any

    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh 'docker build -t application-$(git rev-parse --abbrev-ref HEAD | sed 's/[^a-zA-Z0-9]/-/g'):$BUILD_NUMBER . '
                }
            }    
        }
    }
}
