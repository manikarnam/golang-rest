pipeline{
    agent any
      environment{
        DOCKER_TAG = getDockerTag()
    }
    
    stages{
        stage("Build Image"){
            steps{
                sh "docker build . -t maniengg/golang:${DOCKER_TAG}"
            }
            
        }
        stage('dockerHub & push'){
            steps{
                withCredentials([string(credentialsId: '', variable: 'dockerhub')]) {
                sh "docker login -u maniengg -p ${dockerhub}"
                sh "docker push maniengg/golang:${DOCKER_TAG}"
             }
         }
      }
    }
    
}
    
    def getDockerTag(){
        def tag= sh script: 'git rev-parse HEAD', returnStdout: true
        return tag
    }
  
