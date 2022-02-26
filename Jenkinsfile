pipeline {
    agent any
    environment {
        TEST = 'BRANCH'
    }
    stages {
        stage('create docker image') {
            steps {
                echo "Database engine is ${TEST}"
                sh 'printenv'
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "A='BRANCH'"
                      sh "echo $A"
                      sh "docker build -t application:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
