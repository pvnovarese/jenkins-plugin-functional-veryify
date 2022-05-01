// this is the most basic functional test I could think of with the 
// Anchore Plugin, since it does not seem to have a way to just do
// a simple "system status" or similar action like anchore-cli
// if you're airgapped, you can replace IMAGELINE with a similar 
// trivial image located inside your environment.

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
