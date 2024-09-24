pipeline {
    agent {
        docker {
            image 'node:16'
            args '-u root' // Run as root user inside the container
        }
    }
    stages {
        stage('Build') {
            steps {
                node {
                    npm install --save
                }
            }
        }
    }
    post {
        failure {
            error 'Build failed!'
        }
    }
}