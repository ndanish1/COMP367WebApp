pipeline {
    agent any // Runs on any available Jenkins agent

    stages {
        stage('Checkout') { 
            steps {
                git branch: 'main', url: 'https://github.com/ndanish1/COMP367WebApp.git' // Replace with your Git repo URL
            }
        }

        stage('Build') { 
            steps {
                script {
                    // Run the Maven build for Windows
                    bat 'mvn clean install' // Use bat for Windows
                }
            }
        }

        stage('Test') { 
            steps {
                script {
                    // Run the Maven tests for Windows
                    bat 'mvn test' // Use bat for Windows
                }
            }
        }

        stage('Deploy') { 
            steps {
                echo 'Deploying the application...' 
                // Add your Windows deployment commands here
            }
        }
    }
}

