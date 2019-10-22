pipeline {
    agent { label 'slave_node' }

      stages {
         stage ('Build'){
             steps {
                 script{
                  checkout scm

                  docker.withRegistry('https://us.gcr.io','gcr:gcrproject-256203')  {

                  def app = docker.build("gcrproject-256203/golang345") {
                      app.push()
                   
                    }  
                  }
                 }
             }
         }
      }
}
