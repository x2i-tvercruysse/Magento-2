pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'composer install'
      }
    }
    stage('Static code analysis') {
      steps {
        sh 'vendor/bin/phpcs --standard=MEQP2 --extensions=php,phtml --report=checkstyle --report-file=build/logs/checkstyle.xml .'
      }
    }
    stage('Report') {
      steps {
        echo 'gen report goes here'
      }
    }
  }
}