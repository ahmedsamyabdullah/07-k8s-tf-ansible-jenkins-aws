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
                sh 'echo "Completed!"'
            }
        }
    }
}