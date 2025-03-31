pipeline {
    agent any

    stages {
        stage('Check Node Version') {
            steps {
                script {
                    // Check if Node.js and npm are installed
                    sh 'node -v'
                    sh 'npm -v'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Ensure npm install runs successfully
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Check if the build script exists and runs
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Ensure node is available and can start the server
                    sh 'node -v'  // Check node version
                    sh 'node server'  // Run the server (ensure server.js exists)
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment were successful!'
        }
        failure {
            echo 'Something went wrong in the build or deployment!'
        }
    }
}
