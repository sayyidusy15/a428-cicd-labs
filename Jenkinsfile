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
        input message: 'Lanjutkan ke tahap Deploy?',
              ok: 'Proceed'
    }

    // Penambahan Stage Deploy (Sesuai permintaan revisi)
    stage('Deploy') {
        echo 'Deploying the application...'

        sh './jenkins/scripts/deliver.sh'

        echo 'Application running for 60 seconds...'
        sleep 60

        echo 'Stopping application...'
        sh './jenkins/scripts/kill.sh'
    }
}