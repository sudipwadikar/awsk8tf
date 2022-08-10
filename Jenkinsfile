def mvn
def buildInfo
pipeline {
  agent any
    tools {
      maven 'maven-3.8.6'
      jdk 'java-11'
    }
environment {
        AWS_ACCOUNT_ID="053334083296"
        AWS_DEFAULT_REGION="us-east-1"
        IMAGE_REPO_NAME="sudipwadikar"
        IMAGE_TAG="springtest"
        REPOSITORY_URI = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}"
}
  stages {	
       stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sudipwadikar/awsk8tf.git']]])
            }
        }
        
        stage("Terraform init") {
            steps{
                sh ("terraform init");  
            }
        }
	  
	  /*stage ('K8S Deploy'){
                    //sh 'kubectl apply -f spring-boot.yaml'
	           sh 'kubectl create -f voting-app-deploy.yaml'
		   sh 'kubectl create -f voting-app-service.yaml'
		   sh 'kubectl create -f redis-deploy.yaml'
		   sh 'kubectl create -f redis-service.yaml'
		   sh 'kubectl create -f postgres-deploy.yaml'
		   sh 'kubectl create -f postgres-service.yaml'
		   sh 'kubectl create -f worker-app-deploy.yaml'
		   sh 'kubectl create -f result-app-deploy.yaml'
		   sh 'kubectl create -f result-app-service.yaml'
      } 
       }*/
	  
  }	  	  
}
