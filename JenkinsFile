pipeline { 

    agent any 

    tools { 

        nodejs 'NodeJS 24' // Use the NodeJS configuration from Jenkins 

    } 

    environment { 

        CI = 'true' 

    } 

    stages { 

        stage('Checkout') { 

            steps { 

                git branch: 'main', url: 'https://github.com/blessador/simple-nodejs-app.git' 

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

                    // Deploy script or commands can be added here 

                    bat 'echo Deploying the application...' 

                    //bat 'npm start' 

                    //bat 'node server.js' 

                    bat 'start /B node server.js' 

                    sleep 30 

                    bat 'taskkill /F /IM node.exe' 

                } 

            } 

        } 

        

    } // end of Stages 

 

    post { 

        always { 

            echo 'Cleaning up...' 

            cleanWs() 

        } 

        success { 

            echo 'Pipeline completed successfully.' 

        } 

        failure { 

            echo 'Pipeline failed.' 

        } 

    } 

} 