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
    stage('Deploy to production server') {
      steps {
        timeout(time: 5, unit: 'DAYS')
        input message: 'Approve deployment to production?'
        build job: 'deploy-to-production'
      }
    }
  }
}
