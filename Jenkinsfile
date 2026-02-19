node {
    // Mendefinisikan tool Node.js yang sudah dibuat di Global Tool Configuration
    def nodeHome = tool name: 'Node18', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
    env.PATH = "${nodeHome}/bin:${env.PATH}"

    stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        echo 'Installing dependencies and building...'
        sh 'npm install'
        sh 'npm run build'
    }

    stage('Test') {
        echo 'Running tests...'
        // CI=true memastikan test berhenti setelah selesai (tidak gantung)
        sh 'CI=true npm test -- --watchAll=false'
    }

    stage('Manual Approval') {
        steps {
            input message: 'Lanjutkan ke tahap Deploy?',
                  ok: 'Proceed'
        }
    }

    // Penambahan Stage Deploy (Sesuai permintaan revisi)
    stage('Deploy') {
        echo 'Deploying the application...'
        // Menjalankan script shell untuk deliver
        sh './jenkins/scripts/deliver.sh'
        
        // Memberikan input manual agar pipeline menunggu interaksi user
        input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
        
        // Menjalankan script shell untuk menghentikan proses
        sh './jenkins/scripts/kill.sh'
    }
}