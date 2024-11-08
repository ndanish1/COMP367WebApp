pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = 'docker-hub-credentials'  // Replace with the ID of your Secret Text credentials
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git 'https://github.com/ndanish1/COMP367WebApp'
            }
        }

        stage('Build Maven Project') {
            steps {
                // Run Maven build
                sh 'mvn clean package'
            }
        }

        stage('Docker Login') {
            steps {
                // Login to Docker Hub using Secret Text credentials
                withCredentials([string(credentialsId: "${DOCKER_HUB_CREDENTIALS}", variable: 'DOCKER_PASSWORD')]) {
                    sh 'docker login --username naveeddanish1 --password $DOCKER_PASSWORD'
                }
            }
        }

        stage('Docker Build') {
            steps {
                // Build Docker image
                sh 'docker build -t naveeddanish1/maven-java-webapp .'
            }
        }

        stage('Docker Push') {
            steps {
                // Push Docker image to Docker Hub
                sh 'docker push naveeddanish1/maven-java-webapp'
            }
        }
    }
}
