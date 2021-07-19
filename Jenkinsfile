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
node{

  git branch: "master", url: "https://github.com/robsonbittencourt/jenkins-pipeline-example" 




  stage ('Build Jar') {
    withEnv(["JAVA_HOME=${ tool "java-8" }", "PATH+MAVEN=${ tool "maven" }/bin:${env.JAVA_HOME}/bin"]) {
        sh "mvn clean package -Dmaven.test.skip=true"
    }
  }

  stage ('Build and Deploy DSV image') {
    sh "docker build -t robsonbittencourt/jenkins-pipeline-example:dsv ."
  
    docker.withRegistry("", "registryCredential") {
      sh "docker push robsonbittencourt/jenkins-pipeline-example:dsv"
    }   
  }

  stage ('Deploy app in DSV') {
    sh "docker rm -f app-dsv &>/dev/null && sleep 1 && docker run --name=app-dsv -p 8081:8081 --net jenkins-pipeline-example_default -e SPRING_PROFILES_ACTIVE=dsv -d robsonbittencourt/jenkins-pipeline-example:dsv"
  }
  
}
