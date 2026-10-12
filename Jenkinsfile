pipeline {
  agent any
  environment {
    IMAGE_NAME = 'dimasarya30/simple-app'
    REGISTRY_CREDENTIALS = 'dockerhub-credentials'
  }
  stages {
    stage('Checkout') { 
      steps { 
        checkout scm 
      } 
    }
    stage('Build') { 
      steps { 
        bat 'echo "Build di Windows"' 
      } 
    }
    stage('Build Docker Image') {
      steps { 
        bat 'docker build -t dimasarya30/simple-app:latest .' 
      }
    }
    stage('Push Docker Image') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
          bat 'docker login -u %USER% -p %PASS%'
          bat 'docker push dimasarya30/simple-app:latest'
        }
      }
    }
  }
  post {
    always {
      echo 'Selesai build 🏁'
    }
  }
}
