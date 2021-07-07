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
        sh 'npm start &'
    }
    stage('pushing into s3') {
        echo 'pushing into s3....'
        sh 'aws s3 cp public s3://sampleapp-teja --recursive'
         }
}
