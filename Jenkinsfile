pipeline {
  agent any
  stages {
     stage("test") {
      steps {
        script {
          echo 'testing the application...'
        }
      }
    }
    stage("build") {
      steps {
        script {
          echo 'building the application...'
        }
      }
    }
    stage("deploy") {
      steps {
        script {
          def dockerCmd = 'docker run -p 8080:8080 -d hokage004/demo-app:1.0'
          sshagent(['ec2-server-key']) { 
            sh "ssh -o StrictHostKeyChecking=no ec2-user@15.252.100.91 ${dockerCmd}"
            
          }
        }
      }
    }
  }
} 
