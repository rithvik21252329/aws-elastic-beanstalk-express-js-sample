pipeline {
    agent any
    
    stages {
        stage('Install Dependencies') {
            steps {
                // Checkout the code (if needed)
                checkout scm
                
                // Install dependencies
                sh 'npm install --save'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Add any build steps if needed
                    echo 'No build steps required for this app.'
                }
            }
        }
        
        // You can add more stages here as needed
    }

    post {
        success {
            echo 'Deployment to Elastic Beanstalk was successful!'
        }
        failure {
            echo 'Deployment to Elastic Beanstalk failed!'
        }
    }
}