

// pipeline{
//     agent any
//     environment{
//         IMAGE_NAME = "kiritiaryal"
//         IMAGE_TAG = "latest"
//         REGISTRY_CREDENTIAL = '6a23ecdf-4838-46b9-8e1a-c90f296cb3f6'        
//     }
//     stages{
//        stage('Building image') {
//       steps{
//         script {
//                 dockerImage = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
//                }
//         }
//        }
//        stage('Deploy Image') {
//       steps{
//          script {
//             docker.withRegistry( '', REGISTRY_CREDENTIAL ) {
//             dockerImage.push()
//             }
//           }
//         }
//       }
//     }
// }

node {
    def myImage

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        myImage = docker.build("kiritiaryal/flask_docker:0.0.6")
    }

    // stage('Test image') {
    //     /* Ideally, we would run a test framework against our image. */

    //     myImage.inside {
    //         sh 'echo "Tests passed"'
    //         sh 'ls -ltr'
    //     }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag. */
            withCredentials([usernamePassword( credentialsId: 'docker-hub-credentials')]) {
		
          docker.withRegistry('', 'docker-hub-credentials') {
          sh "docker login -u KiritiAryal -p hItm@ndo1"
           myImage.push("0.0.6")
           myImage.push("latest")
         }
            
        }
 }
