pipeline {
    agent { label 'slave_node' }

      stages {
          stage('Build image') {
              steps{
                checkout scm
                 docker.withRegistry('https://eu.gcr.io', 'gcr:[9ed113a1f5a5985b7643cab16c481e2abfc593f5]') {
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

