pipeline {
  agent any
  stages {
    stage('Test') {
      agent {
        node {
          label 'Alfred'
        }
        
      }
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
      steps {
        echo 'Reporting'
      }
    }
  }
  environment {
    DEBUG = 'False'
    LV_VERSION = '2017'
  }
}