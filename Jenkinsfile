node {
    // Tahap 1: Persiapan (Clone Source Code)
    stage('Checkout') {
        checkout scm
    }

    // Tahap 2: Install Dependensi
    stage('Install Dependencies') {
        // Menggunakan Docker container node:lts-slim untuk build
        sh 'npm install'
    }

    // Tahap 3: Build Aplikasi (Kriteria Wajib)
    stage('Build') {
        echo 'Building the React Application...'
        sh 'npm run build'
    }

    // Tahap 4: Unit Testing (Kriteria Wajib)
    stage('Test') {
        echo 'Running Unit Tests...'
        // CI=true digunakan agar test di React tidak masuk ke mode watch
        sh 'CI=true npm test'
    }
}