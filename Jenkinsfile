pipeline {
    agent { label 'slave_node' }

      stages {
         stage ('Build'){
             steps {
                 script{
                  checkout scm

                  docker.withRegistry('https://us.gcr.io','gcr:gcrproject-257509')  {

                  def app = docker.build('gcrproject-257509/golang-declarativepipeline') 
                      app.push()
                   
                    }  
                  }
                 }
             }
         }
      }

