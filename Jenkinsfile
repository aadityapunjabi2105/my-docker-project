pipeline {
    agent any

    environment {
        DOCKER_HUB_USERNAME = 'your-dockerhub-username'
        DOCKER_HUB_PASSWORD = 'your-dockerhub-password'
        IMAGE_NAME = 'your-dockerhub-username/your-image-name'  // Update with your Docker image name
    }

    stages {
        stage('Checkout') {
            steps {
                // Pull the latest code from GitHub
                git 'https://github.com/your-username/my-docker-project.git'  // Replace with your GitHub repo URL
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                // Log in to Docker Hub
                sh "echo $DOCKER_HUB_PASSWORD | docker login -u $DOCKER_HUB_USERNAME --password-stdin"
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push the Docker image to Docker Hub
                sh "docker push $IMAGE_NAME"
            }
        }
    }
}
