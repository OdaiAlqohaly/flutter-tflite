pipeline {
    agent { docker { image 'flutter:latest' } }

    stages {
        stage('Build') {
            steps {
                sh 'flutter build'
            }
        }
        stage('Test') {
            steps {
                sh 'flutter test'
            }
        }
        stage('Deploy') {
            when {
                expression { env.DEPLOY_ENABLED == 'true' }
            }
            steps {
                sh 'flutter deploy'
            }
        }
    }
}

// Environment Variables
environment {
    DEPLOY_ENABLED = 'true'
}