pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'flutter pub get'
                    sh 'flutter build'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh 'flutter test'
                }
            }
        }
        stage('Deploy') {
            when {
                expression { params.DEPLOY_ENABLED }
            }
            steps {
                script {
                    sh 'flutter deploy'
                }
            }
        }
    }

    parameters {
        boolean(name: 'DEPLOY_ENABLED', defaultValue: true, description: 'Enable deployment?')
    }
}