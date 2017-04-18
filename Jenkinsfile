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
vendor/bin/phpcs --standard=MEQP2 --extensions=php,phtml --report=checkstyle --report-file=build/logs/checkstyle.xml --ignore=vendor --runtime-set ignore_errors_on_exit 1 --runtime-set ignore_warnings_on_exit 1 .'''
      }
    }
    stage('Report') {
      steps {
        checkstyle(healthy: '100', unHealthy: '999', pattern: 'build/logs/checkstyle.xml')
      }
    }
  }
}