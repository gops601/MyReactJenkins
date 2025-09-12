pipeline {
    agent any

    environment {
        IMAGE_NAME = "gops601/pipeline {
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
                    bat "docker stop flask-container || exit 0"
                    bat "docker rm flask-container || exit 0"
                    bat "docker run -d --name flask-container -p 5175:5173 ${IMAGE_NAME}:${TAG}"
                }
            }
        }
    }
}"
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
                    bat "docker stop flask-container || exit 0"
                    bat "docker rm flask-container || exit 0"
                    bat "docker run -d --name flask-container -p 5175:5173 ${IMAGE_NAME}:${TAG}"
                }
            }
        }
    }
}
