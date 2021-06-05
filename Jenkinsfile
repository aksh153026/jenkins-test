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

    stage('Install node modules') {
      steps {
        sh "npm install"
      }
    }

    stage("Test") {
      steps {
        sh "npm run test-headless"
      }
    }

    stage("Build") {
      steps {
        sh "npm run build --prod"
      }
    }
    
    stage("Copy") {
     steps {
        sh "cp -a /var/lib/jenkins/workspace/angular-pipeline/dist/jenkins-test/. /var/www/jenkins_test/html/"
     }
    }
    }
}
