pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        tool(name: 'apache-maven-3.5.2', type: 'maven')
        script {
          if (isUnix()) {
            sh "mvn package"
          } else {
            bat "mvn package"
          }
        }

      }
    }
  }
}