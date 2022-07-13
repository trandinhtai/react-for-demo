pipeline {
  agent any
  // agent {
    // node {
    //   label 'my-label'
    // }
  // }
  stages {

    stage ('Install dependencies') {
      steps {
        nodejs(nodeJSInstallationName: 'nodejs 8.9.4') {
          sh 'echo "Installing..."'
          sh 'npm install'
          sh 'echo "Install dependencies successfully."'
          sh 'ls -al'
        }
      }
    }
    
    stage ('Test') {
      steps {
        nodejs(nodeJSInstallationName: 'nodejs 8.9.4') {
          sh 'echo "Run unit test..."'
          sh 'npm test'
          sh 'echo "Run unit test successfully."'
          sh 'ls -al'
        }
      }
    }

    stage ('Build') {
      step {
        nodejs(nodeJSInstallationName: 'nodejs 8.9.4') {
          sh 'echo "Build application..."'
          sh 'npm test'
          sh 'echo "Build application successfully."'
          sh 'ls -al'
        }
      }
    }

    stage ('Result') {
      agent any
      steps {
         sh 'echo "Starting to build docker image"'
         sh 'docker build -t pick-color:v1 -f docker/Dockerfile .'
      }
    }
  }
}