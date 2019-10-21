pipeline {
    agent { label 'slave_node' }

      stages {
          stage('Build image') {
             steps{
              def app = docker.build("[gcrproject-256203/golang-pipeline]")
             }
          }
  
   stage('Push image') {
     docker.withRegistry('gcrproject-256203', 'golaang@gcrproject-256203.iam.gserviceaccount.com]') {
     app.push("${env.BUILD_NUMBER}")
     app.push("latest")
     }
   }
 }
}

