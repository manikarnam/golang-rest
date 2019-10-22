pipeline {
    agent { label 'slave_node' }
  stages {
        stage("Fetch repository") {
            steps {
                    git 'https://github.com/manikarnam/golang-rest.git'
                }
            }
     stage('Build image') {
        app = docker.build("[gcrproject-256203]/[golangpipeline]")
     }
    stage('Push image') {
   docker.withRegistry('https://eu.gcr.io', 'gcr:[9ed113a1f5a5985b7643cab16c481e2abfc593f5]') {
    app.push("${env.BUILD_NUMBER}")
    app.push("latest")
      }
    }
  }
}
