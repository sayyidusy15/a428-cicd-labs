pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'react-app',
                    url: 'https://github.com/sayyidusy15/a428-cicd-labs.git'
            }
        }

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
