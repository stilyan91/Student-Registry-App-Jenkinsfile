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

}
