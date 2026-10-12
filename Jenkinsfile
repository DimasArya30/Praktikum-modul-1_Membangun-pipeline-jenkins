pipeline {
  agent any
  environment {
    REGISTRY_CREDENTIALS = 'dockerhub-credentials'
    // Path asli DockerDesktop di laptop ACER
    PATH = "C:\\Users\\ACER\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin;${env.PATH}"
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
        withCredentials([usernamePassword(credentialsId: REGISTRY_CREDENTIALS, usernameVariable: 'USER', passwordVariable: 'PASS')]) {
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
