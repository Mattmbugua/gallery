pipeline {
  agent any

  stages {
    // Stage to install dependencies
    stage('Installing the dependencies') {
      steps {
        script {
          // Install npm dependencies
          sh 'npm install'
        }
      }
    }

    // Stage to deploy to Render
    stage('Deploying to Render') {
      steps {
        script {
          // Deploy to Render (replace with actual deploy command if different)
          sh 'node server'
        }
      }
    }
  }

  post {
    success {
      echo "Deployment success!"
    }
    failure {
      echo "Deployment failure!"
    }
  }
}
