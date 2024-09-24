pipeline {
    agent {
        docker {
            image 'node:16'
            args '-u root' // Run as root user inside the container
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
    }
    post {
        failure {
            error 'Build failed!'
        }
    }
}