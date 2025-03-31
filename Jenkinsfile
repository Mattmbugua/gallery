pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:$PATH"  // Adjust this path if needed
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Node Version') {
            steps {
                script {
                    sh 'node -v'  // Check if Node is correctly installed and accessible
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'  // Install dependencies
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'npm run build'  // Replace with your build command
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'node server'  // Replace with your deploy/start command
                }
            }
        }
    }

    post {
        always {
            echo 'This is where you can handle post-deployment actions.'
        }
        success {
            echo 'Deployment was successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
