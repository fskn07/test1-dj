pipeline {
    agent any

    stages {
        stage('create docker image') {
            environment {
                BRANCH=BRANCH.toLowerCase()
            }
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh 'docker build -t application-$BRANCH:$BUILD_NUMBER . '
                }
            }    
        }
    }
}
