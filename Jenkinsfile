pipeline {
    agent any
       environment {
          CC = """${sh(
          returnStdout: true,
          script: '$BRANCH_NAME'
            )}"""
    }
    stages {
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
