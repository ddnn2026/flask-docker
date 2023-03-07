pipeline {

  agent none

  environment {
    DOCKER_IMAGE = "ddnn2026/flask-docker"
  }

  stages {
    stage("Test") {
      agent {
          docker {
            image 'python:3.10-buster'
            args '-u 0:0 -v /tmp:/root/.cache'
          }
      }
      steps {
        sh "pip install poetry"
        sh "poetry install"
        sh "poetry run pytest"
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