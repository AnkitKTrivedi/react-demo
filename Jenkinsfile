pipeline {
  agent any

  tools {
    nodejs 'Node-20' // Match what you configured in Jenkins
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/AnkitKTrivedi/react-demo.git'
      }
    }

    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Run tests') {
      steps {
        sh 'npm test -- --watchAll=false'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Archive Build Output') {
      steps {
        archiveArtifacts artifacts: 'build/**', fingerprint: true
      }
    }

    // Optional deployment stage can be added here
  }

  post {
    success {
      echo 'Build and Test Successful!'
    }
    failure {
      echo 'Something went wrong!'
    }
  }
}
