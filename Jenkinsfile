pipeline {
  agent {
    node {
      label 'vueclient'
    }

  }
  stages {
    stage('Prepare') {
      parallel {
        stage('Prepare') {
          steps {
            sh 'cd /data/web/jv-awesome && sudo git stash'
          }
        }

        stage('Echo Message') {
          steps {
            echo 'Build Start'
          }
        }

      }
    }

    stage('Git Pull') {
      agent any
      environment {
        para1 = '1'
      }
      steps {
        sh 'cd /data/web/jv-awesome  && sudo git pull'
      }
    }

    stage('Build') {
      steps {
        sh 'cd /data/web/jv-awesome && sudo tnpm i --needlock && sudo tnpm run build'
      }
    }

    stage('Send Msg') {
      steps {
        echo 'Job Done'
      }
    }

    stage('Test') {
      agent {
        node {
          label 'master'
        }

      }
      environment {
        CI = 'true'
      }
      steps {
        sh '''echo \'Testing\'
echo \'Testing Done\''''
      }
    }

  }
  environment {
    testenv = 'testvalue'
  }
  
  post {
    success {
       echo 'sucess' 
    }
  }
}
