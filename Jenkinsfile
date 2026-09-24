pipeline {
  agent any 
  tools {
    maven 'maven-3.9'
  }
  stages {
    stage("build jar") {
      steps {
        echo 'building the application...'
        sh 'mvn package'
      }
    }
     stage("build image") {
      steps {
        echo 'building the docker image...'
        withCredentials([usernamePassword(credentialId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER' )]) {
          sh 'docker build -t hokage004/demo-app:2.0 .'
          sh 'docker login -u $USER -p $PASS'
          sh 'docker push hokage004/demo-app:2.0'
        }
      }
    }
    stage("deploy") {
      steps {
        echo 'deploying the application...'
      }
    }
  }
}
