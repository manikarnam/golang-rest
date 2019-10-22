pipeline {
    agent { label 'slave_node' }

      stages {
         stage('Build image') {
             steps {
                 docker.withRegistry('https://us.gcr.io', 'gcr:gcrproject') {
                   def image = docker.build("[gcrproject-256203]/[golang12]")
                      image.push("${env.BUILD_NUMBER}")
                      image.push("latest")
           
                
            }
          }
        }
      }
}
