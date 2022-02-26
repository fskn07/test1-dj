pipeline {
    agent any

    stages {
        stage('create docker image') {
            steps {
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
