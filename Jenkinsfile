pipeline {
    agent { label 'slave_node' }

      stages {
         stage('Build image') {
             
              docker.withRegistry('https://us.gcr.io', 'gcr:google-container-registry-project') {
             def myContainer = docker.build("[gcrproject-256203]/[golang12]")
            myContainer.push("${env.BUILD_NUMBER}")
            myContainer.push("latest")
        }
       }
      }
}
