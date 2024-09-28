pipeline {
    agent {
        docker {
            image 'node:16'
        }
    }
    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    checkout scm
                    sh 'npm install --save'
                }
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
                    sh 'npm install -g snyk'
                    sh 'snyk test'
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment to Elastic Beanstalk was successful!'
        }
        failure {
            echo 'Deployment to Elastic Beanstalk failed!'
            error 'Halting pipeline due to critical vulnerabilities.'
        }
    }
}