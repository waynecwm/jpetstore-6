pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Start Build Step'
        sh 'mvn clean install -Dlicense.skip=true'
        echo 'Build step complete'
      }
    }
    stage('Testing stage') {
      parallel {
        stage('Testing stage') {
          steps {
            sh 'mvn sonar:sonar -Dsonar.host.url=http://<IP address>:8081 -Dlicense.skip=true'
          }
        }
        stage('SonarQube Test') {
          steps {
            echo 'The tester is ${TESTER}'
            sleep 10
          }
        }
      }
    }
  }
}