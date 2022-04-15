env.STAGEBUILD = ''
env.STAGEPUSH = ''
env.STAGEPDEPLOY = ''
pipeline {
    agent any
    stages {
        stage('Building docker image') {
            steps {
                echo 'Start building docker image'
                dir ('docker') {
                      sh ('docker build -t ncdevreg.ml:5000/nginxtest-$GIT_BRANCH:$BUILD_NUMBER .')
                }
            }
            post {
         	    failure {
         		      script {
         			        env.STAGEBUILD = "Failure at stage BUILDING docker image"
                         }
         	            }
                    }
        }
        stage('Push docker image to local registry') {
            steps {
                echo 'Login docker registry and push docker image'
                withCredentials([usernamePassword(credentialsId: 'localregistry',
                                                  passwordVariable: 'localregistryPassword',
                                                  usernameVariable: 'localregistryUser')])
                  {
                    sh ('docker login https://ncdevreg.ml:5000 -u $localregistryUser -p $localregistryPassword')
                    sh ('docker push ncdevreg.ml:5000/nginxtest-$GIT_BRANCH:$BUILD_NUMBER')
                  }
           }
           post {
         	   failure {
         		     script {
         			       env.STAGEPUSH = "Failure at stage PUSH docker image"
                        }
         	           }
                   }
         }
         stage('deploy'){
           steps {
                dir ('docker') {
                        sh ('docker stack deploy --compose-file docker-compose.yml stack-nginxtest --with-registry-auth') }

                }
           post {
             failure {
              	 script {
              			 env.STAGEPDEPLOY = "Failure at deploy stage"
                        }
              	     }
                }
           }
   }
  

     
   }
