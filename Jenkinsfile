pipeline {
  agent any
  stages {
    stage('Build war file') {
      steps {
        sh 'mvn clean package'
      }
      post {
        success {
          archiveArtifacts artifacts: '**/*.war'
        }
      }
    }
  }
}
