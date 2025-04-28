pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS 16'
    }
    stages{
      stage('Checkout') {
            steps {
                
                git url: 'https://github.com/Mattmbugua/gallery.git', branch: 'master'

                echo "Doing the Github step"
            }
        }
         stage('Ensure Software is installed') {
            steps {
                    
                    
                    sh 'node --version'
                    sh 'npm --version'
                    echo "npm installation check"
                
            }
        }
        
        stage('Building') {
            steps {
                    
                    // Ensure npm is installed and install project dependencies
                    sh 'npm install'
                
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
                        subject: "Jenkins Build Failed: Testing Stage.",
                        body: "The build failed at the Test stage. Please check the Jenkins job for more details.",
                        to: 'mathewmbugua2015@gmail.com' 
                    )
                }
            }

            
        }
        
        stage('Deploy') {
            steps {
                script {
            
                    // Deployment of the website
                   

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
            
        }
        failure {
            echo "Pipeline failed!"



            slackSend(channel: 'mathew_ip1', message: "❌ Build failed.Try building again!")
            
        }
    }
}