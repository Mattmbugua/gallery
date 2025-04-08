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
        stage('Building') {
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
        stage('Testing') {
            steps {
                
                    // Run the tests with npm
                    sh 'npm run test'
                
            }
             post {
                failure {
                    // Send email if the tests fail
                    emailext(
                        subject: "Jenkins Build Failed: Test Stage.",
                        body: "The build failed at the Test stage. Please check the Jenkins job for more details.",
                        to: 'mathewmbugua2015@gmail.com' // Change this to your email address
                    )
                }
            }

            
        }

        
        
        
        
    }
   post {
        success {
            echo "Pipeline completed successfully!"
            //send slack message 
             slackSend(channel: 'mathew_ip1', message: "✅ Build ${env.BUILD_ID} succeeded! View it here: ${https://gallery-01hj.onrender.com}")
            //Send success email
            emailext(
                subject: "Jenkins Build Successful",
                body: "The Jenkins pipeline has completed successfully.All stages passed.",
                to: 'mathewmbugua2015@gmail.com' // Change this to your email address
            )
        }
        failure {
            echo "Pipeline failed!"



            slackSend(channel: 'mathew_ip1', message: "❌ Build failed.Try building again!")
            //Send failure email
            emailext(
                subject: "Jenkins Build Failed!",
                body: "The Jenkins pipeline has failed. Please check the Jenkins job for more details.",
                to: 'mathewmbugua2015@gmail.com' // Change this to your email address
            )
        }
    }
}