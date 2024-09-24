pipeline {
    agent {
        docker {
            image 'node:16'
            args '-u root' // Run as root user inside the container
        }
    }
    post {
        failure {
            error 'Build failed!'
        }
    }
}