pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            args '-u root'
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test -- --watchAll=false'
            }
        }
    }
}
