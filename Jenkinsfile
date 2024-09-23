pipeline {
    agent {
        docker {
            image 'node:16'
            args '-u root'
        }
    }
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install --save'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'snyk test'
            }
        }
    }
    post {
        failure {
            error('Build failed due to vulnerabilities!')
        }
    }
}