
pipeline {
      agent none
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
            agent { node {label 'master'}
              args "-u 0:0"
            }
            steps {
              withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')])
              {
              sh 'echo $DOCKER_PASSWORD | docker login --username $DOCKER_USERNAME --password-stdin'
              sh 'docker push ${docker_image}:latest'
              }

              sh "docker image rm ${docker_image}:latest"
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



