pipeline {
  agent any
  stages {
    stage('Test') {
      steps {
        echo 'Analyser'
      }
    }
    stage('Unit Tests') {
      steps {
        echo 'Unit Tests'
      }
    }
    stage('Build') {
      steps {
        echo 'Build'
      }
    }
    stage('Report') {
      parallel {
        stage('Report') {
          steps {
            echo 'Reporting'
          }
        }
        stage('Temp') {
          steps {
            echo 'Temporary Files'
          }
        }
      }
    }
  }
  environment {
    DEBUG = 'False'
    LV_VERSION = '2017'
    RETRY_COUNT = 5
  }
}