pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('docker image'){
            steps{
                sh "docker build -t ${IMAGE_NAME}:latest ."
            }
        }
    }
}