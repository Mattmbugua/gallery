
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