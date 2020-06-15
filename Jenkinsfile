pipeline {
  agent any
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
  }
}
