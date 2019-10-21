pipeline {
    agent { label 'slave_node' }

      stages {
        stage('Build image') {
         app = docker.build("[gcrproject-256203]/[golang-pipeline]")
       }
  
   stage('Push image') {
     docker.withRegistry('golaang@gcrproject-256203.iam.gserviceaccount.com', 'gcrproject-256203]') {
     app.push("${env.BUILD_NUMBER}")
     app.push("latest")
     }
   }
 }
}
