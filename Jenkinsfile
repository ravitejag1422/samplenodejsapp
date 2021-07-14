/*node {
    stage('Build') {
        echo 'checkout code...'
        branch=$BRANCH  
        environments=$env
        checkout scm
    }
    stage('Test') {
        sh 'node --version'
    }
    /*stage('Deploy') {
        echo 'Deploying....'
        sh 'npm install'
        sh 'npm start &'
    }
    stage('pushing into s3') {
        echo 'pushing into s3....'
        sh 'aws s3 cp public s3://sampleapp-teja --recursive'
         }
}
*/
pipeline {
    agent any

    parameters {
        // booleanParam, choice, file, text, password, run, or string
        booleanParam(defaultValue: true, description: '', name: 'booleanExample')
        string(defaultValue: "TEST", description: 'What environment?', name: 'stringExample')
        text(defaultValue: "This is a multiline\n text", description: "Multiline Text", name: "textExample")
        choice(choices: 'US-EAST-1\nUS-WEST-2', description: 'What AWS region?', name: 'choiceExample')
        password(defaultValue: "Password", description: "Password Parameter", name: "passwordExample")
    }

    stages {
        stage("foo") {
            steps {
                echo "booleanExample: ${params.booleanExample}"
                echo "stringExample: ${params.stringExample}"
                echo "textExample: ${params.textExample}"
                echo "choiceExample: ${params.choiceExample}"
                echo "passwordExample: ${params.passwordExample}"
            }
        }
    }
}
