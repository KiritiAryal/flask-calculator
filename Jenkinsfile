pipeline{
    agent any
    environment{
        IMAGE_NAME = "kiritiaryal"
        REGISTRY_CREDENTIAL = 'docker-hub-credentials'        
    }
    stages{
       stage('Building image') {
      steps{
        script {
                dockerImage = docker.build("${IMAGE_NAME}:0.0.6")
               }
        }
       }
       stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', ${REGISTRY_CREDENTIAL} ) {
            dockerImage.push("0.0.6")
            dockerImage.push("latest")
            }
          }
        }
      }
    }
}

// node {
//     def myImage

//     stage('Build image') {
//         /* This builds the actual image; synonymous to
//          * docker build on the command line */

//         myImage = docker.build("kiritiaryal/flask_docker:0.0.6")
//     }

//     // stage('Test image') {
//     //     /* Ideally, we would run a test framework against our image. */

//     //     myImage.inside {
//     //         sh 'echo "Tests passed"'
//     //         sh 'ls -ltr'
//     //     }
//     }

//     stage('Push image') {
//         /* Finally, we'll push the image with two tags:
//          * First, the incremental build number from Jenkins
//          * Second, the 'latest' tag. */
//             withCredentials([usernamePassword( credentialsId: 'docker-hub-credentials')]) {
		
//           docker.withRegistry('', 'docker-hub-credentials') {
//           sh "docker login -u KiritiAryal -p hItm@ndo1"
//            myImage.push("0.0.6")
//            myImage.push("latest")
//          }
            
//         }
//  }
