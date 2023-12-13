pipeline {
    agent any

    environment {
        // Define environment variables if needed
        DOCKER_REGISTRY = "docker.io"
        DOCKER_REPO = "dhanaboi/first-app"
        DOCKER_IMAGE_TAG = "latest"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control (e.g., Git)
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                script {
                    docker.build("${DOCKER_REGISTRY}/${DOCKER_REPO}:${DOCKER_IMAGE_TAG}")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push the Docker image to the registry
                script {
                    docker.withRegistry("${DOCKER_REGISTRY}", 'dokerPassUser') {
                        docker.image("${DOCKER_REGISTRY}/${DOCKER_REPO}:${DOCKER_IMAGE_TAG}").push()
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Build and push successful!'
        }
        failure {
            echo 'Build or push failed!'
        }
    }
}
