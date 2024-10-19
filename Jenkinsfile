pipeline {
    agent any // This means that the pipeline can run on any available agent

    stages {
        stage('Checkout') { // Stage to checkout the source code from the repository
            steps {
                git 'https://github.com/ndanish1/COMP367WebApp.git' // Replace with your repo URL
            }
        }

        stage('Build') { // Stage to build the application
            steps {
                script {
                    // Run the Maven build
                    sh 'mvn clean install' // For Unix/Linux
                    // Uncomment the next line for Windows:
                    // bat 'mvn clean install'
                }
            }
        }

        stage('Test') { // Stage to run tests
            steps {
                script {
                    // Run the Maven tests
                    sh 'mvn test' // For Unix/Linux
                    // Uncomment the next line for Windows:
                    // bat 'mvn test'
                }
            }
        }

        stage('Deploy') { // Stage to deploy the application
            steps {
                echo 'Deploying the application...' // Replace this with your actual deployment steps
                // Add your deployment commands here if needed
            }
        }
    }
}
