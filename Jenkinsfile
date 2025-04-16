pipeline{
    agent any

    // Set Variables
    environment {
        APP_NAME = "NodeJs app"
    }

    stages{
        // Clean WorkSpace Before Build
        stage('Clean Before Build'){
            steps{
                cleanWs()
            }
        }
        stage('Build in Docker'){
            agent{
                docker{
                    images 'node:18'
                    reuseNode true    // Option
                }
            }
            steps{
                sh '''
                    echo "Building APP ...."
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
            }
        }
    }
    // Clean After Pipeline Completed
    post{
        always{
            cleanWs()
        }
    }
}