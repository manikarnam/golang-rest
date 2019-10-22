pipeline {
    agent { label 'slave_node' }

      stages {
         stage('Build image') {
             steps {
              def image = docker.build("[gcrproject-256203]/[golang12]")
              docker.withRegistry('https://us.gcr.io', 'gcr:gcrproject') {
           
                image.push("${env.BUILD_NUMBER}")
                image.push("latest")
            }
          }
        }
      }
}
