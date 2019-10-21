pipeline {
    agent { label 'slave_node' }

      stages {
         stage('Build image') {
              def app = docker.build("[gcrproject-256203]/[golang12]")
            }
        stage('Push image') {
           docker.withRegistry('https://eu.gcr.io', 'gcr:[gcrproject-9ed113a1f5a5985b7643cab16c481e2abfc593f5]') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
     }
   }
}
