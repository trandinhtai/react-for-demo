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
          sh 'ls -al'
          sh 'echo "Installing..."'
          sh 'npm run build'
          sh 'echo "Install dependencies successfully.'
        }
      }
    }
    
    stage ('Test') {
      steps {
        nodejs(nodeJSInstallationName: 'nodejs 8.9.4') {
          sh 'ls -al'
          sh 'echo "Run unit test..."'
          sh 'npm test'
          sh 'echo "Run unit test successfully.'
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