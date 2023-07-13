
pipeline {
      agent any
      environment {
        docker_image = "tbnghiep11/node-app"
      }
      stages {
        stage("build") {
            steps {
            sh 'docker build -t ${docker_image}:latest .'
          }          
        }
        stage("push image")
        {
            steps {
              withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')])
              sh 'echo $DOCKER_PASSWORD | docker login --username $DOCKER_USERNAME --password-stdin'
              sh 'docker push ${docker_image}:latest'
              
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



