pipeline {
    agent any
    environment {
        TEST = 'BRANCH'
    }
    stages {
        stage('create docker image') {
            steps {
                echo "Database engine is ${TEST}"
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application-@BRANCH_NAME:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
