pipeline {
    agent { label 'slave_node' }

      stages {
          stage('Build image') {
             steps{
                 docker.withRegistry('gcrproject-256203', 'golaang@gcrproject-256203.iam.gserviceaccount.com]') {
               def app = docker.build("[gcrproject-256203/golang-pipeline]")
                   app.push("${env.BUILD_NUMBER}")
                   app.push("latest")
             }
          }
   
     }
   }
 }
  // stage('Push image') {
     
   
//}

