pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from your repository
                git 'https://github.com/MaXimeHH/Jenkins.git'
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
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mvn deploy'
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
