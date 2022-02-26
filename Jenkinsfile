pipeline {
    agent any

    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh 'docker build -t (application-BRANCH_NAME | tr '[:upper:]' '[:lower:]'):$BUILD_NUMBER . '
                }
            }    
        }
    }
}
