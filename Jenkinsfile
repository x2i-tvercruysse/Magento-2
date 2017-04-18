pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building module'
        sh 'composer install'
      }
    }
    stage('QA') {
      steps {
        echo 'phpcs goes here'
      }
    }
    stage('Report') {
      steps {
        echo 'gen report goes here'
      }
    }
  }
}