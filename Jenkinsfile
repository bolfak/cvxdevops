pipeline {
  agent any
  environment {
    APP_VERSION = '${BUILD_NUMBER}'
    DOCKER_REGISTRY = 'bolfak'
    APP_NAME = 'myfirstwebapp'
    dockerImage = ''
    REGISTRY_CREDENTIALS = 'DockerHub'
  }
  stages {
    stage('Restore Dependencies') {
      steps {
        sh 'dotnet restore'
      }
    }
    stage('Build') {
      steps {
        sh 'dotnet build'
      }
    }
    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build "${DOCKER_REGISTRY}/${APP_NAME}:${APP_VERSION}"
        }
      }
    }
    stage('Deploy Docker Image') {
      steps {
        script {
          docker.withRegistry( '', REGISTRY_CREDENTIALS) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
