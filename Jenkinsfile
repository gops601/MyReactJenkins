pipeline {
    agent any

    environment {
        IMAGE_NAME = "gops601/react-login-app"
        TAG = "latest"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${TAG}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker stop react-container || true"
                    sh "docker rm react-container || true"
                    sh "docker run -d --name react-container -p 5175:5173 ${IMAGE_NAME}:${TAG}"
                }
            }
        }
    }
}
