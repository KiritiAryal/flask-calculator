pipeline{
    agent any
    environment{
        IMAGE_NAME = "kiritiaryal/flask_docker"     
    }
    stages{
       stage('Building image') {
      steps{
        script {
                dockerImage = docker.build("${IMAGE_NAME}")
               }
        }
       }
       stage('Deploy Image') {
      steps{
         script {
             docker.withRegistry( '', 'docker-hub-credentials') {
             echo "Pushing..."
             dockerImage.push("0.0.7")
             dockerImage.push("latest")
             echo "Pushed!!"
            }
          }
        }
      }
    }
}

