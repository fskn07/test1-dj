pipeline {
    agent any
    stages {
        stage('create docker image') {
            steps {
                sh "NAME=$BRANCH_NAME"
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application-$NAME:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
