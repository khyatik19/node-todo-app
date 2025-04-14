pipeline {
    agent any
 
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
        IMAGE_NAME = 'khyatik19/docker_image'
    }
 
    stages {
        stage('Clone Code') {
            steps {
                checkout scm
            }
        }
 
        stage('Build Docker Image') {
            steps {
                script {
                    if (!fileExists('Dockerfile')) {
                        error "Dockerfile not found!"
                    }
                    sh "docker build -t $IMAGE_NAME ."
                }
            }
        }
 
        stage('Push to DockerHub') {
            steps {
                script {
                    sh "echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin"
                    sh "docker push $IMAGE_NAME"
                }
            }
        }
 
        stage('Run Container from DockerHub') {
            steps {
                sh "docker pull $IMAGE_NAME"
                sh 'docker run -d -p 8081:8080 khyatik19/docker_image'
            }
        }
    }
}

 
 