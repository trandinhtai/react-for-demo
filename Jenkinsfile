pipeline {
  agent any
  // agent {
    // node {
    //   label 'my-label'
    // }
  // }
  stages {
    stage ('Cloning Git') {
      steps {
        git 'https://github.com/HoangPhu98/react-for-demo.git'
      }
    }

    stage ('Build & Test') {
      steps {
        nodejs(nodeJSInstallationName: 'nodejs 8.9.4', configId: '<config-file-provider-id>') {
          sh 'ls -al'
          sh 'echo "Build source code..."'
          sh 'npm run build'
          sh 'echo "Build source code successfully.'
        }
      }
    }
    
    stage ('Test') {
      steps {
        nodejs(nodeJSInstallationName: 'nodejs 8.9.4', configId: '<config-file-provider-id>') {
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