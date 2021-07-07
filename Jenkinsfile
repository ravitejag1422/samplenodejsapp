node {
    stage('Build') {
        echo 'checkout code...'
        checkout scm
    }
    stage('Test') {
        sh 'node --version'
    }
    stage('Deploy') {
        echo 'Deploying....'
        sh 'npm install'
        sh 'npm build'
    }
}
