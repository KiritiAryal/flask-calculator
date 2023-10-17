#!groovy

pipeline{
    agent any
    environment{
        
        registry = "KiritiAryal/flask_docker"
        registryCredential = 'KiritiAryal'        
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