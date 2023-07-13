
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



