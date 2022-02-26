pipeline {
    agent any
    environment {
        QWE = sh '$BRANCH_NAME'
    }
    stages {
        
        stage('create docker image') {
            steps {
                echo $QWE
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application-$BRANCH_NAME:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
