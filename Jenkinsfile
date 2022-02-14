pipeline {
    agent any

    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh 'docker build "app:${env.BUILD_ID}" .  '
                }
            }    
        }
    }
}
