pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('checkout'){
            steps{
                sh "docker build -t ${IMAGE_NAME}:latest ."
            }
        }
    }
}