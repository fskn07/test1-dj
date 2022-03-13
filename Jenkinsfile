env.STAGEBUILD = ''
env.STAGEMESSAGE = ''
pipeline {
    agent any
    stages {
        stage('create docker image') {
            steps {
                dir ('docker8') {
                      sh "docker build -t application:$GIT_BRANCH-$BUILD_NUMBER . "
                }
            } 
            post {
         	failure {
         		script {
         			env.STAGEBUILD = "Failure at stage BUILDING1 docker image"}
         	}
         }
        }
     stage('building2') {
            steps {
                dir ('docker7') {
                      sh "docker build -t application:$GIT_BRANCH-$BUILD_NUMBER . "
                }
            } 
            post {
         	  failure {
                  script {
         			env.STAGEMESSAGE = "Failure at stage BUILDING2"
                  }
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
