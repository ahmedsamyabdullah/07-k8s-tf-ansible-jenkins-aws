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

        // Build Stage
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
                    echo "Building APP ...."
                    node --version
                    npm --version
                    npm install --cache $WORKSPACE/.npm
                    npm run build
                '''
            }
        }

        // Test Stage
        stage('Test'){
            agent{
                docker{
                    image 'node:18'
                    reuseNode true 
                }
            }
            steps{
                sh '''
                    test -f build/index.html
                    npm test
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