pipeline {
  agent any  
  environment {
    //put your environment variables
    doError = '0'
    DOCKER_REPO = "12345678.dkr.ecr.ap-south-1.amazonaws.com/${JOB_NAME}"
    AWS_DEFAULT_REGION = "us-east-1"
    CHART_DIR="$JENKINS_HOME/workspace/helm-integration/helm"
    HELM_RELEASE_NAME = "api-service"
    ENV= """${sh(
  		returnStdout: true,
  		script: 'declare -n ENV=${GIT_BRANCH}_env ; echo "$ENV"'
    ).trim()}"""
  }
    options {
        buildDiscarder(logRotator(numToKeepStr: '20')) 
  }   
  stages {
    stage ('Build and Test') {
      steps {
        sh '''
        docker build \
        -t ${DOCKER_REPO}:${BUILD_NUMBER} .
        #put your Test cases
        echo 'Starting test cases'
        '''    
      }
    }  
    
  }
}
