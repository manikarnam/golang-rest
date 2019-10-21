pipeline {
    agent { label 'slave_node' }

      stages {
         stage('Build image') {
              def app = docker.build("[gcrproject-256203]/[golang12]")
            }
        stage('Push image') {
           docker.withRegistry('https://eu.gcr.io', 'gcr:[gcrproject-256203]') {
         //  app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
     }
   }
}
