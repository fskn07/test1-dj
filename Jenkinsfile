pipeline {
    agent any
    stages {
        stage('create docker image') {
            steps {
                sh "$BRANCH_NAME.toLowerCase()"
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application-$BRANCH_NAME:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
