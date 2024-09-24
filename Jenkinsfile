pipeline {
    agent {
        docker {
            image 'node:16'
            args '--privileged -v /var/run/docker.sock:/var/run/docker.sock'
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