pipeline {
    agent any
    environment {
        QWE = sh 'git rev-parse --abbrev-ref HEAD'
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
