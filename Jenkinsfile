pipeline {
  agent any
  stages {
    stage('Build war file') {
      steps {
        sh 'mvn clean package'
      }
      post {
        success {
          echo 'Archiving'
          archiveArtifacts artifacts: '**/*.war'
        }
      }
    }
    stage('Deploy to stage server') {
      steps {
        build job: 'deploy-to-staging'
      }
    }
  }
}
