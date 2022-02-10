pipeline {
    agent any

    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker2') {
                      sh 'docker build . hellogit'
                }
            }
             steps {
                echo '--------Run docker---------'
                dir ('docker2') {
                      sh 'docker run -p 5000:5000 hellogit'
                }
            }     
        }
    }
}
