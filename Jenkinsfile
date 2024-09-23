pipeline {
    agent {
        docker { image 'node:16' }
    }
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install --save'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'npm audit'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'snyk test'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '*/target/.jar', allowEmptyArchive: true
            junit '*/target/surefire-reports/.xml'
        }
        failure {
            error 'Build failed!'
        }
    }
}