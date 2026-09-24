def gv

pipeline {
  agent any 
  tools {
    maven 'maven-3.9'
  }
  stages {
    stage("init") {
      steps {
        script {
          gv = load "script.groovy"
        }
      }
    }
    stage("build jar") {
      steps {
        gv.buildJar()
      }
    }
     stage("build image") {
      steps {
        gv.buildImage()
        }
      }
    }
    stage("deploy") {
      steps {
        gv.deployApp()
      }
    }
  }

