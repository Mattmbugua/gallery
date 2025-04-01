pipeline {
    agent any
    // environment {
    //     // Define environment variables (e.g., email configuration or other secrets)
    //     EMAIL_RECIPIENTS = "mathewmugua2015@gmail.com"  // Replace with the email you want to notify on failure
    // }
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
        stage('Run Tests') {
            steps {
                
                    // Run the tests with npm
                    sh 'npm run test'
                
            }

            post {
                failure {
                    // Send an email notification if the tests fail
                    mail to: 'mathewmugua2015@gmail.com',
                         subject: "Build failed: ${currentBuild.fullDisplayName}",
                         body: "The build failed during the 'Run Tests' stage. Please check the logs. 9q8yegfqygf"
                }
            }
        }

        
        
        
        
    }
    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed!"
            
            // Send an email notification if the pipeline fails
            emailext(
                to: "${EMAIL_RECIPIENTS}",
                subject: "Jenkins Build Failed: ${currentBuild.fullDisplayName}",
                body: "The build failedsldfjkvjklbnsdfkjpphjsfdb. Please check the Jenkins logs for more details.",
                mimeType: 'text/html'
            )
        }
    }
}