pipeline {
    agent any

    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "A=git rev-parse --abbrev-ref HEAD"
                      sh "echo $A"
                      sh "docker build -t application:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
