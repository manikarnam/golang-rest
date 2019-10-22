pipeline {
    agent { label 'slave_node' }

      stages {
         stage('Build image') {
            myContainer = docker.build("[gcrproject-256203]/[golang12]")
            }
       stage('Push images') {
        docker.withRegistry('https://us.gcr.io', 'gcr:google-container-registry-project') {
            myContainer.push("${env.BUILD_NUMBER}")
            myContainer.push("latest")
        }
       }
      }
}
