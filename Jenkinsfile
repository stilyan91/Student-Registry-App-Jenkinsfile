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

        stage('Build Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: '24fe69f3-28f0-4d45-ac05-ec208f174e44', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    bat """docker build -t dimosoftuni/student:1.0.0 .
                        docker login -u %DOCKER_USERNAME% --password %DOCKER_PASSWORD%
                        docker push stilyan9/student:1.0.0"""
                }
            }
        }
        stage('Deploy Image') {
            steps {
              script {
                    // Prompt for input approval
                    input("Deploy to production?") 
                }
                withCredentials([usernamePassword(credentialsId: '24fe69f3-28f0-4d45-ac05-ec208f174e44', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    bat """docker pull stilyan9/student:1.0.0
                    docker run -d -p 8081:8081 stilyan9/student:1.0.0 """
                }
            }
        }
    }
}