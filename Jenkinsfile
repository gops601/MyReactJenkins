pipeline {
  agent any

  environment {
    IMAGE_NAME = 'react-vite-app'     // change if you want
    TAG        = "${env.BUILD_NUMBER}"// auto-incremented build tag
    CONTAINER  = 'react-app'
    PORT_MAP   = '5177:5173'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Docker Build') {
      steps {
        bat 'docker --version'
        bat """
          docker build -t %IMAGE_NAME%:%TAG% .
        """
      }
    }

    stage('Stop Old Container (if any)') {
      steps {
        // Ignore errors if container doesn't exist
        bat 'docker stop %CONTAINER% || exit 0'
        bat 'docker rm %CONTAINER% || exit 0'
      }
    }

    stage('Run New Container') {
      steps {
        bat """
          docker run -d --name %CONTAINER% -p %PORT_MAP% %IMAGE_NAME%:%TAG%
        """
      }
    }

    
  }

  post {
    always {
      echo "Built %IMAGE_NAME%:%TAG% and (re)started container %CONTAINER% on port %PORT_MAP%"
      bat 'docker ps -a'
    }
  }
}