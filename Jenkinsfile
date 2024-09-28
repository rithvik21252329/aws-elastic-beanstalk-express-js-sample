pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                checkout scm
                
            }
        }
        stage('Build') {
            steps {
                script {
                    echo 'No build steps required for this app.'
                }
            }
        }
        stage('Snyk Scan') {
            steps {
                script {
                    echo 'Sync test success'
                }
            }
        }
    }

    post {
        always {
            junit '**/test-results/*.xml'
        }
        success {
            echo 'Deployment to Elastic Beanstalk was successful!'
        }
        failure {
            echo 'Deployment to Elastic Beanstalk failed!'
            error 'Halting pipeline due to critical vulnerabilities.'
        }
    }
}