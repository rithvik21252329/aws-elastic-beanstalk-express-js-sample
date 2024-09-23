pipeline {
    agent {
        docker {
            image 'node:16' // Using Node.js version 16 as the build agent
            args '-u root:root' // Run as root user
        }
    }
    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Install project dependencies from package.json
                    sh 'npm install --save' // This installs express and any other dependencies
                }
            }
        }
        stage('Run Security Scan') {
            steps {
                script {
                    // Scan for vulnerabilities using Snyk
                    // Ensure Snyk is installed in your Node.js environment
                    sh 'npm install -g snyk' // Install Snyk CLI globally
                    sh 'snyk test' // Test for vulnerabilities
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build a Docker image for the application
                    sh 'docker build -t aws-elastic-beanstalk-app .' // Builds the Docker image
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Run the Docker container in detached mode, mapping the appropriate ports
                    sh 'docker run -d -p 3000:3000 aws-elastic-beanstalk-app' // Exposes the app on port 3000
                }
            }
        }
    }
    post {
        failure {
            // Notify or halt the pipeline if a security vulnerability is found
            echo 'Pipeline failed due to security vulnerabilities detected. Please review the logs.'
            error('Pipeline halted due to vulnerabilities.')
        }
    }
}
