pipeline {
  agent any
  environment {
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
        /* Menggunakan path lengkap docker.exe di Windows */
        bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" build -t dimasarya30/simple-app:latest .' 
      }
    }
    stage('Push Docker Image') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
          bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" login -u %USER% -p %PASS%'
          bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" push dimasarya30/simple-app:latest'
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
