node {
    agent {
        docker {
            label 'dockeragent'
            image 'jenkins/jnlp-agent-node'
        }
    }
    stages {     
        stage ('Prepare') {
            steps {
                script {
                    echo "TESTING DOCKER"
                    node --version
                }
            }
        }
    }
}