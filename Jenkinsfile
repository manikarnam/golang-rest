pipeline{
    agent any
      environment{
        DOCKER_TAG = getDockerTag()
    }
    
    stages{
        stage("Build Image"){
            steps{
                sh "sudo docker build . -t maniengg/golang:${DOCKER_TAG}"
            }
            
        }
        stage('dockerHub & push'){
            steps{
               withCredentials([string(credentialsId:'docker-hub', variable:'dockerHubPwd')]) {
                sh "sudo docker login -u maniengg -p ${dockerHubPwd}"
                sh "sudo docker push maniengg/golang:${DOCKER_TAG}"
             }
         }
      }
    }
    
}
    
    def getDockerTag(){
        def tag= sh script: 'git rev-parse HEAD', returnStdout: true
        return tag
    }
  
