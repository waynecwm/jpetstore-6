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
        stage('SonarQube Test') {
          steps {
            sh 'mvn sonar:sonar -Dsonar.host.url=http://<IP address>:8081 -Dlicense.skip=true'
          }
        }
        stage('Print Tester Credentials') {
          steps {
            echo 'The tester is ${TESTER}'
            sleep 10
          }
        }
        stage('Print build number') {
          steps {
            echo 'This is build number ${BUILD_ID}'
          }
        }
      }
    }
  }
}