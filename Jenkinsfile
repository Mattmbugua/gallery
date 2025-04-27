pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS 16'
    }
    stages{
      stage('Checkingout') {
            steps {
                
                git url: 'https://github.com/Mattmbugua/gallery.git', branch: 'master'
            }
        }
        
        stage('Build') {
            steps {
            
                    // Ensure npm is installed and install project dependencies
                    sh 'npm install'
                
            }
        }


       
        stage('Test ') {
            steps {
                
                    // Run the tests with npm
                    sh 'npm run test'
                
            }
             post {
                failure {
                    // Send email if the tests fail
                    emailext(
                        subject: "Jenkins Build Failed: Testing Stage.",
                        body: "The build failed at the Test stage. Please check the Jenkins job for more details.",
                        to: 'mathewmbugua2015@gmail.com' // Change this to your email address
                    )
                }
            }

            
        }
        
        stage('Deploy') {
            steps {
                script {
            
                    // Ensure npm is installed and install project dependencies
                   

                    sh 'curl -X POST https://api.render.com/v1/services/srv-cvlcl8bipnbc73di56r0/deploys -H "Authorization: Bearer $rnd_BhT1p7UZ7huNC3vwhljXFdgQFQHI" -H "Content-Type: application/json" -d "{}"'



                }
                
            }
        }

        
        
        
        
    }
   post {
        success {
            echo "Pipeline completed successfully!"
            //send slack message 
             slackSend(channel: 'mathew_ip1', message: "✅ Build ${env.BUILD_ID} succeeded! View it here: https://gallery-01hj.onrender.com")
            //Send success email
            emailext(
                subject: "Jenkins Build Successful",
                body: "The Jenkins pipeline has completed successfully.All stages passed.",
                to: 'mathewmbugua2015@gmail.com' 
            )
        }
        failure {
            echo "Pipeline failed!"



            slackSend(channel: 'mathew_ip1', message: "❌ Build failed.Try building again!")
            //Send failure email
            emailext(
                subject: "Jenkins Build Failed !",
                body: "The Jenkins pipeline has failed. Please check the Jenkins job for more details.",
                to: 'mathewmbugua2015@gmail.com' // Change this to your email address
            )
        }
    }
}