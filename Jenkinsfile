pipeline {
    agent any

    environment {
        IMAGE_NAME = "abdullahosama911/flask-app"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Abdullah5497/DockerTask'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:latest", ".")
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-cred') {
                        docker.image("${IMAGE_NAME}:latest").push()
                    }
                }
            }
        }
    }
}
