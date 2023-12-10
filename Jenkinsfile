pipeline {
    agent any

    stages {
        stage('Repo Checkout') {
            steps {
                checkout scm
            }
        }
        stage('NPM Install') {
            steps {
                bat 'npm install'
            }
        }
        stage('Run Integration Tests') {
            steps {
                bat 'npm run test'
            }
        }
    }

    post {
        always {
            // Actions to perform after the pipeline runs, e.g., clean up, send notifications
        }
        success {
            // Actions to perform if the pipeline was successful
        }
        failure {
            // Actions to perform if the pipeline failed
        }
    }
}
