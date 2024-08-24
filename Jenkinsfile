pipeline {
  agent any
  triggers {
    pollSCM('*/2 * * * *')
  }
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
    stage('Deploy') {
      parallel {
        stage('Deploy to stage server') {
          steps {
            sh 'cp **/*.war /srv/tomcat-staging/webapps
          }
      }
        stage('Deploy to production server') {
          sh 'cp **/*.war /srv/tomcat-production/webapps
        }
    }
  }
}
