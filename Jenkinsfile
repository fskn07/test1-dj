pipeline {
    agent any
    stages {
        stage('create docker image') {
            steps {
                sh "$BRANCH_NAME | perl -ne 'print lc'"
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application-$BRANCH_NAME | perl -ne 'print lc':$BUILD_NUMBER . "
                }
            }    
        }
    }
}
