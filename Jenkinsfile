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
        sh '''mkdir -p build/logs
mkdir -p build/logs
vendor/bin/phpcs --standard=MEQP2 --extensions=php,phtml --report=checkstyle --report-file=build/logs/checkstyle.xml --ignore=vendor .'''
      }
    }
    stage('Report') {
      steps {
        step(
            [
              $class: 'CheckStylePublisher',
              canComputeNew: false,
              defaultEncoding: '',
              healthy: '100',
              pattern: 'build/logs/checkstyle.xml',
              unHealthy: '999'
            ]
          )
      }
    }
  }
}
