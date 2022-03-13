pipeline {
    agent any
    stages {
        stage('create docker image') {
            steps {
                echo '--------Start building image---------'
                dir ('docker') {
                      sh "docker build -t application:$GIT_BRANCH-$BUILD_NUMBER . "
                }
            } 
            post {
         	failure {
         		script {
         			env.STAGEBUILD = "Failure at stage BUILDING docker image"}
         	}
         }
        }
     stage('message') {
            steps {
                   echo 'Hello my Jenkins'
            } 
            post {
         	failure {
         		script {
         			env.STAGEMESSAGE = "Failure at stage MESSAGE"}
         	}
         }
        }
    }
    post {
     success { 
        withCredentials([string(credentialsId: 'tokenmyjenkinsbot', variable: 'TOKEN'), string(credentialsId: 'chatidmyjenkins', variable: 'CHAT_ID')]) {
        sh  ("""
            curl -s -X POST https://api.telegram.org/bot${TOKEN}/sendMessage -d chat_id=${CHAT_ID} -d parse_mode=markdown -d text='*${env.JOB_NAME}* : POC *Branch*: ${env.GIT_BRANCH} *Build* : OK'
        """)
        }
     }
     failure {
        withCredentials([string(credentialsId: 'tokenmyjenkinsbot', variable: 'TOKEN'), string(credentialsId: 'chatidmyjenkins', variable: 'CHAT_ID')]) {
        sh  ("""
            curl -s -X POST https://api.telegram.org/bot${TOKEN}/sendMessage -d chat_id=${CHAT_ID} -d parse_mode=markdown -d text='*${env.JOB_NAME}* : POC  *Branch*: ${env.GIT_BRANCH} *Build* : not OK ${env.STAGEBUILD} ${env.STAGEMESSAGE}'
        """)
        }
     }

 }
}
