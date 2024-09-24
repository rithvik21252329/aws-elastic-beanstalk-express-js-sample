pipeline {
    agent {
        docker {
            image 'node:16'
            args '-u root:root' // optional: run as root
        }
    }
    
    stages {
        stage('Install Dependencies') {
            steps {
                // Checkout the code (if needed)
                checkout scm
                
                // Install dependencies
                sh 'npm install --save'
            }
        }
        
        // You can add more stages here as needed
    }

    post {
        failure {
            error 'Build failed!'
        }
    }
}