pipeline {
    sh 'A=git rev-parse --abbrev-ref HEAD.toLowerCase()'
    def TEST = $A;
    agent any

    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application-${TEST}:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
