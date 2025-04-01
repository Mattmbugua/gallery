// pipeline {
//     agent any

//     environment {
//         PATH = "/usr/local/bin/node:$PATH"  // Adjust this path if needed
//     }

//     stages {
//         stage('Checkout') {
//             steps {
//                 checkout scm
//             }
//         }

//         stage('Check Node Version') {
//             steps {
//                 script {
//                     sh 'node -v'  // Check if Node is correctly installed and accessible
//                 }
//             }
//         }

//         stage('Install Dependencies') {
//             steps {
//                 script {
//                     sh 'npm install'  // Install dependencies
//                 }
//             }
//         }

//         stage('Build') {
//             steps {
//                 script {
//                     sh 'npm run build'  // Replace with your build command
//                 }
//             }
//         }

//         stage('Deploy') {
//             steps {
//                 script {
//                     sh 'node server'  // Replace with your deploy/start command
//                 }
//             }
//         }
//     }

//     post {
//         always {
//             echo 'This is where you can handle post-deployment actions.'
//         }
//         success {
//             echo 'Deployment was successful!'
//         }
//         failure {
//             echo 'Deployment failed!'
//         }
//     }
// }
pipeline {
    agent any
    tools {
        nodejs 'NodeJS 16'
    }
    stages{
        stage('Check npm') {
                steps {
                    sh 'npm --version'
                    }
            }
            // Stage to install dependencies
        stage('Install Dependencies') {
            steps {
            
                    // Ensure npm is installed and install project dependencies
                    sh 'npm install'
                
            }
        }


        // Stage to update the landing page (add "MILESTONE 2")
        stage('Update Landing Page') {
            steps {
                
                    // Append or modify the landing page HTML to add "MILESTONE 2"
                    sh '''echo '<h1 style="font-size: 50px; color: red;">MILESTONE 2</h1>' >> public/index.html'''
                
            }
        }

        
        
        
        
        }
}
