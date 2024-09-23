pipeline {
    agent any {
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
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
    }
    post {
        failure {
            error('Build failed due to vulnerabilities!')
        }
    }
}