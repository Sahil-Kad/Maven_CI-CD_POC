pipeline {
  agent any
  stages {
    stage('Build Application') { 
      steps {
        bat 'mvn clean install'
      }
    }
    stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypointCreds')
        ENV_CREDENTIALS = credentials('envCreds')
      }
      steps {
        bat 'mvn clean deploy -DmuleDeploy -DClientId=${ANYPOINT_CREDENTIALS_USR} -DClientSecret=${ANYPOINT_CREDENTIALS_PSW} -DGrantType=client_credentials -Dplatform.client_id=${ENV_CREDENTIALS_USR} -Dplatform.client_secret=${ENV_CREDENTIALS_PSW}' 
      }
    }
  }
}

