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
        stage('Checkout'){
            steps{
                checkout scm
            }
        }
        stage('Build in Docker'){
            agent{
                docker{
                    image 'node:18'
                    reuseNode true    // Option
                }
            }
            steps{
                sh '''
                    rm -rf node_modules package-lock.json
                    npm cache clean --force
                    mkdir -p $WORKSPACE/.npm
                    npm config set cache $WORKSPACE/.npm --global
                    echo "Building APP ...."
                    node --version
                    npm --version
                    npm install
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