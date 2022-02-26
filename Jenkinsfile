pipeline {
    agent any

    stages {
       environment {
          CC = """${sh(
          returnStdout: true,
          script: 'git rev-parse --abbrev-ref HEAD'
            )}"""
    }
        stage('create docker image') {
            steps {
                echo "Database engine is ${CC}"
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application-$BRANCH_NAME:$BUILD_NUMBER . "
                }
            }    
        }
    }
}
