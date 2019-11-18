pipeline {
  agent any
  stages {
    stage('stage1') {
      steps {
        pwd(tmp: true)
        fileExists '/tmp/test'
      }
    }

    stage('stage2') {
      agent any
      environment {
        para1 = '1'
      }
      steps {
        waitUntil() {
          sh 'python2.7 --version'
        }

      }
    }

  }
}