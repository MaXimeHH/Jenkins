pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from your repository
                git 'https://github.com/votre-utilisateur/votre-projet.git'
            }
        }

        stage('Build') {
            steps {
                // Build the Maven project
                sh 'mvn -v'
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run tests
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your artifact or do further processing here
                // Example: sh 'mvn deploy'
            }
        }
    }

    post {
        success {
            // This block will be executed when the pipeline is successful
            echo 'Build successful!'
        }

        failure {
            // This block will be executed when the pipeline fails
            echo 'Build failed!'
        }

        always {
            // This block will always be executed regardless of the pipeline outcome
            // You can do cleanup or any other actions here
        }
    }
}
