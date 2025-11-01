pipeline {
    agent {
        docker {
            image 'flutter:latest'
            args '--user root'
        }
    }

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
                expression { env.DEPLOY_ENABLED == 'true' }
            }
            steps {
                script {
                    sh 'flutter deploy'
                }
            }
        }
    }

    environment {
        DEPLOY_ENABLED = 'true'
    }
}