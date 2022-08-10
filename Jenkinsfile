def mvn
def buildInfo
pipeline {
  agent any
    tools {
      maven 'maven-3.8.6'
      jdk 'java-11'
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
	  
	stage("Terraform plan") {
            steps{
                sh ("terraform plan");  
            }
        }  
	 
	stage("Terraform apply") {
            steps{
                sh ("terraform apply -auto-approve");  
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
