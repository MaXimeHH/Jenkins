pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('Tests') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    script {
                        junit 'target/surefire-reports/*.xml'
                        step([$class: 'JUnitResultArchiver', testResults: 'target/surefire-reports/*.xml'])
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
