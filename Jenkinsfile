pipeline {
    agent any
    environment {
        TEST = $BRANCH_NAME
    }
    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application-$TEST:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
