pipeline {
    agent {
        docker {
            // Menggunakan image node yang memang didesain untuk lingkungan Docker
            image 'node:18-bullseye-slim' 
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    }
}