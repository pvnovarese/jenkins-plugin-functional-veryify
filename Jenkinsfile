pipeline {
  environment {
    IMAGELINE = "docker.io/busybox:latest"
  } // end environment 
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        checkout scm
      } // end steps
    } // end stage "checkout scm"
    stage('Analyze with Anchore plugin') {
      steps {
        writeFile file: 'anchore_images', text: IMAGELINE
        anchore name: 'anchore_images', forceAnalyze: 'false', bailOnFail: false
      } // end steps
    } // end stage "analyze with anchore plugin"
  } // end stages
} // end pipeline 
