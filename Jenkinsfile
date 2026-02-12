node {
    stage('Checkout') {
        checkout scm
    }

    stage('Install Dependencies') {
        // Kita pakai npm langsung, tanpa membungkusnya dengan Docker
        sh 'npm install'
    }

    stage('Build') {
        sh 'npm run build'
    }

    stage('Test') {
        sh 'CI=true npm test'
    }
}