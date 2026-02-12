node {
    stage('Checkout') {
        checkout scm
    }

    stage('Install Dependencies') {
        // Menggunakan npm langsung tanpa kontainer docker
        sh 'npm install'
    }

    stage('Build') {
        sh 'npm run build'
    }

    stage('Test') {
        sh 'CI=true npm test'
    }
}