pipeline {
     agent { label 'slave_node' }
     // agent none
      stages {
         stage ('Build') {
             steps {
                 script {
                  checkout scm

                  docker.withRegistry('https://us.gcr.io','gcr:gcrproject-256203') {

                  def app = docker.build("gcrproject-256203/golanggoogle") 
                      app.push()
                   
                    }  
                  }
                 }
             }
         }
      }

