pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'Melakukan checkout dari SCM...'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Mulai build aplikasi'
                bat 'echo "Build selesai ✅"'
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Membangun Docker image...'
                bat 'echo "Docker Image berhasil dibuat ✅"'
            }
        }
        stage('Push Docker Image') {
            steps {
                echo 'Push image ke Docker Hub...'
                bat 'echo "Docker Image berhasil di-push ✅"'
            }
        }
    }
    post {
        always {
            echo 'Selesai build 🏁'
        }
    }
}
