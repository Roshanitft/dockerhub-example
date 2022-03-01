pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('hubdockertft')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t roshanitft/dp-alpine:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push roshanitft/dp-alpine:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
