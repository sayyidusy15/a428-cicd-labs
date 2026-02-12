node {
    // Mendefinisikan tool Node.js yang sudah kamu buat di Global Tool Configuration
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
}