pipeline {
    agent {
        docker {
            image 'node:18'
        }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node -v'
            }
        }
    }
}
