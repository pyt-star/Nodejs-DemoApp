pipeline {

    agent any

    tools {
        nodejs 'NodeJS24'
    }

    environment {
        CI = 'true'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/pyt-star/Nodejs-DemoApp.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    bat 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    bat 'npm test'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    bat 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    bat 'echo Deploying the application...'

                    bat 'start "" /B node server.js'

                    sleep 30

                    bat 'C:\\Windows\\System32\\taskkill.exe /F /IM node.exe'
                }
            }
        }

    }

    post {

        success {
            echo 'Pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed.'
        }
    }
}
