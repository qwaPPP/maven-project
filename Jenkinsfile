pipeline {
  agent any
  stages {
    stage('Build war file') {
      sh 'mvn clean package'
      post {
        success {
          archiveArtifacts artifacts: '**/*.war'
        }
      }
    }
  }
}
