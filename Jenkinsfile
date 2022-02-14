pipeline {
   agent any

   environment {
     // You must set the following environment variables
     // ORGANIZATION_NAME
     // YOUR_DOCKERHUB_USERNAME (it doesn't matter if you don't have one)
     YOUR_DOCKERHUB_USERNAME = "hvny"
     ORGANIZATION_NAME = "vny-ci-cd-demo"
     SERVICE_NAME = "fleetman-mongodb"     
     REPOSITORY_TAG="${YOUR_DOCKERHUB_USERNAME}/${ORGANIZATION_NAME}-${SERVICE_NAME}:${BUILD_ID}"
   }

   stages {
      
      stage('Build') {
         steps {
            sh '''echo No build required for Mongodb'''
         }
      }

      stage('Build and Push Image') {
         steps {
           sh 'docker login -u "hvny" -p "7702305501@Dhub" docker.io'
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
