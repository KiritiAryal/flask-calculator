#!groov

pipeline{
    agent any
    environment{
        IMAGE_NAME = "kiritiaryal"
        IMAGE_TAG = "latest"
        REGISTRY_CREDENTIAL = '6a23ecdf-4838-46b9-8e1a-c90f296cb3f6'        
    }
    stages{
       stage('Building image') {
      steps{
        script {
                
                dockerImage = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
               }
        }
       }
       stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', REGISTRY_CREDENTIAL ) {
            dockerImage.push()
            }
          }
        }
      }
    }
}