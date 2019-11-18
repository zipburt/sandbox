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
      steps {
        waitUntil() {
          sh 'python2.7 --version'
        }

      }
    }

  }
}