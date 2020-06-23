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
        /*stage('Deploy to k8s'){
	       steps{
		      sh "chmod +x changeTag.sh"
			  sh "./changeTag.sh ${DOCKER_TAG}"
			  sshagent(['kops-machine']){
			  sh "scp -o StrictHostKeyChecking=no service.yml node-app-pod.yml ubuntu@52.66.70.61:/ubuntu/"
			  script{
			   try{
			       sh "ssh ubuntu@52.62.1.7 kubectl appy -f ."
			     catch (error){
		                sh "ssh ubuntu@52.62.1.7 kubectl create -f ."
                 }
              }
           }
        }
      }
     }  */
    }
    
 }
    
    def getDockerTag(){
        def tag= sh script: 'git rev-parse HEAD', returnStdout: true
        return tag
    }
  
