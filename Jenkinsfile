pipeline {
  agent any
  environment {
    REGISTRY_CREDENTIALS = 'dockerhub-credentials'
    // Menambahkan lokasi standar Docker Windows ke PATH eksekusi Jenkins
    PATH = "C:\\Program Files\\Docker\\Docker\\resources\\bin;C:\\Program Files\\Docker\\Docker;${env.PATH}"
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
