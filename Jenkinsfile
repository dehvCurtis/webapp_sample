pipeline {
  agent any
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
          echo "PATH = ${PATH}"
          echo "M2_HOME = ${M2_HOME}"
        '''
      }
    }
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Tomcat-Deploy') {
      steps {
        sshagent(['tomcat_server']) {
          sh 'scp -o StrictHostKeyChecking=no /tmp/test.txt ubuntu@13.52.102.33:/tmp/test.txt'
        }
      }
    }
  }
}
