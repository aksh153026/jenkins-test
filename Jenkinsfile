pipeline {
  agent {
    docker { image 'node:latest' }
  }
  stages {
    stage('Checkout SCM') {
       steps {
        git branch: 'jenkins_test', url: 'git@github.com:aksh153026/jenkins-test.git'
       }
    }
    stage('Install') {
      steps { sh 'npm install' }
    }
 
    stage('Test') {
      parallel {
        stage('Static code analysis') {
            steps { sh 'npm run-script lint' }
        }
        stage('Unit tests') {
            steps { sh 'npm run-script test' }
        }
      }
    }
 
    stage('Build') {
      steps { sh 'npm run-script build' }
    }
  }
}
