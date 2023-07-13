
pipeline {
agent any
environment {
  DOCKER_IMAGE = "tbnghiep11/node-app"
  DOCKER_TAG = 'latest'
  DOCKERHUB_CREDENTIALS = credentials ("docker-hub")
}
    stages{
      stage("build")
      {
        steps {
          sh 'docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} .'
        }
      }
      stage ("push")
      {
        steps {
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
          sh 'docker push ${DOCKER_IMAGE}:${DOCKER_TAG}'
        }
      }
    }
      post {
    success {
      echo "SUCCESSFUL"
    }
    failure {
      echo "FAILED"
    }
  }
    }



