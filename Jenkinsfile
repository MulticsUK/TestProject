pipeline {
  agent any
  stages {
    stage('Configure') {
      agent any
      environment {
        PATH = 'c:\\python'
      }
      steps {
        echo 'Configuration'
        bat(script: '\\scripts\\configure.bat', returnStatus: true)
      }
    }
    stage('Test') {
      steps {
        timeout(time: 3, unit: 'MINUTES') {
          retry(count: 5) {
            powershell '\\scripts\\flakey-UnitTests.ps1'
          }
          
        }
        
      }
    }
  }
  environment {
    LV_VERSION = '2017'
    LV_PROJ = '\\source\\MyProject.lvproj'
    ACCESS_KEY = credentials('my-secret-key')
  }
  post {
    always {
      echo 'One way or another, I have finished'
      postClean()
      
    }
    
    success {
      echo 'I succeeeded!'
      
    }
    
    unstable {
      echo 'I am unstable :/'
      
    }
    
    failure {
      echo 'I failed :('
      emailext(attachLog: true, body: 'You Broke the build!', compressLog: true, subject: 'You Broke the build', to: 'info@multics.co.uk')
      
    }
    
    changed {
      echo 'Things were different before...'
      
    }
    
  }
  options {
    timeout(time: 1, unit: 'HOURS')
  }
}