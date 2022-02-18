pipeline {
   agent any

   environment {
     // You must set the following environment variables
     // ORGANIZATION_NAME
     // YOUR_DOCKERHUB_USERNAME (it doesn't matter if you don't have one)'
     
     ORGANIZATION_NAME = "vny-org-cicd"
     SERVICE_NAME = "fleetman-mongodb"
     ECR_URI = "794077140502.dkr.ecr.us-east-2.amazonaws.com/fleetman-mongodb"
     REPOSITORY_TAG ="${ECR_URI}:${BUILD_ID}"
   }

   stages {
      
      stage('Build') {
       
         steps {
            sh '''echo No build required for Mongodb'''
         }
      }

      stage('Build and Push Image') {
         steps {
           sh 'aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 794077140502.dkr.ecr.us-east-2.amazonaws.com' 
           sh 'echo No docker image for Mongodb'
         }
      }

      stage('Deploy to Cluster') {
          steps {
                // withKubeConfig(contextName: 'default', credentialsId: '9a91910b-c106-47bc-bc12-757dfd2ad6a2', namespace: 'default', serverUrl: '${KUBERNETES_API_SERVER}') {
                    sh 'envsubst < ${WORKSPACE}/deploy.yaml | kubectl apply -f -'
                // }
          }
      }
   }
}
