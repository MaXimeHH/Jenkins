pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Tests') {
            steps {

                sh 'mvn test'
            }
         post {
                always{
                    xunit (
                        thresholds: [ skipped(failureThreshold: '0'), failed(failureThreshold: '0') ],
                        tools: [ BoostTest(pattern: 'target/surefire-reports/*.xml') ]
                    )
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
