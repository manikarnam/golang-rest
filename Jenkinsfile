pipeline {
    agent { label 'slave_node' }

      stages {
          stage('Build image') {
              steps{
                checkout scm
                 docker.withRegistry('https://us.gcr.io', 'gcr:golaang@gcrproject-256203.iam.gserviceaccount.com]') {
                 def app = docker.build("[gcrproject-256203]/[golang-pipeline]")
                   app.push("${env.BUILD_NUMBER}")
                   app.push("latest")
             }
          }
   
     }
   }
 }
  // stage('Push image') {
     
   
//}

