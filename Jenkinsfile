pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Build the Dart application using Flutter
                    sh 'flutter build'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests for the Dart application
                    sh 'flutter test'
                }
            }
        }
        stage('Deploy') {
            when {
                expression { env.DEPLOY_ENABLED == 'true' }
            }
            steps {
                script {
                    // Deploy the Dart application using Flutter
                    sh 'flutter deploy'
                }
            }
        }
    }
    environment {
        DEPLOY_ENABLED = 'true'
    }
}