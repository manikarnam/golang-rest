pipeline {
    agent { label 'slave_node' }

      stages {
         stage('Build image') {
             steps {
              docker.withRegistry('https://us.gcr.io', 'gcr:gcrproject') {
             def myContainer = docker.build("[gcrproject-256203]/[golang12]")
            myContainer.push("${env.BUILD_NUMBER}")
            myContainer.push("latest")
            }
          }
        }
      }
}
