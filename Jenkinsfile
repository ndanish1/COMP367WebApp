pipeline {
    agent any

    tools {
        maven 'MAVEN3'  // This is the tool installation name that you've configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub repository (assuming 'main' is the branch)
                git branch: 'main', url: 'https://github.com/ndanish1/COMP367WebApp.git'
            }
        }

        stage('Build Maven Project') {
            steps {
                // Use Windows cmd shell for executing Maven commands
                bat 'mvn clean install'
            }
        }

        stage('Unit Test') {
            steps {
                // Run unit tests (if any exist in the Maven project)
                bat 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                // Build the Docker image
                bat 'docker build -t naveeddanish1/maven-java-webapp .'
            }
        }

        stage('Docker Hub Push') {
            steps {
                withCredentials([string(credentialsId: 'docker-hub-credentials', variable: 'DOCKER_PASS')]) {
                    // Log in to Docker Hub
                    bat 'docker login -u naveeddanish1 -p %DOCKER_PASS%'
                    // Push the Docker image to Docker Hub
                    bat 'docker push naveeddanish1/maven-java-webapp'
                }
            }
        }
    }
}
