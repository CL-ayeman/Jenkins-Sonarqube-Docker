pipeline {
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('docker')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t shaikhayeman95/jenk-dock .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push shaikhayeman95/jenk-dock'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
