#!groovy

pipeline{
    agent any
    environment{
        
        registry = "KiritiAryal/flask_docker"
        registryCredential = '6a23ecdf-4838-46b9-8e1a-c90f296cb3f6'        
    }
    
    stages{
       stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":latest"
          }
        }
       }
       stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
            }
          }
        }
      }
    }
}