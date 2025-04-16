pipeline{
    agent any
    stages{
        // Clean WorkSpace Before Build
        stage('Clean Before Build'){
            steps{
                cleanWS()
            }
        }
        stage('Build'){
            steps{
                sh 'echo "Completed!'
            }
        }
    }
    // Clean Workspace After Pipeline
    post{
        always{
            cleanWS()
        }
    }
    }
}