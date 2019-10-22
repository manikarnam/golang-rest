pipeline {
    agent { label 'slave_node' }
    def app
      stages {
        stage('Build image') {
        app = docker.build("gcrproject-256203/golang123:${env.BUILD_NUMBER}")
     }
    stage('Push image') {
   docker.withRegistry('https://us.gcr.io','gcr:gcrproject-256203') {
    app.push()
      }
    }
  }
}
