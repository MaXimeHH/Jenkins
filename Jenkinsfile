pipeline {
    agent any

    stages {
        stage('Install Maven') {
            steps {
                // Télécharger le fichier zip de Maven
                sh 'curl -O https://repo.maven.apache.org/maven2/org/apache/maven/apache-maven/3.9.2/apache-maven-3.9.2-bin.zip'

                // Décompresser le fichier zip
                sh 'unzip apache-maven-3.9.2-bin.zip'

                // Déplacer Maven dans un répertoire approprié
                sh 'mv apache-maven-3.9.2 /opt/maven'
            }
        }

        stage('Build') {
            steps {
                // Configure les variables d'environnement pour Maven
                environment {
                    MAVEN_HOME = '/opt/maven'
                    PATH = "${MAVEN_HOME}/bin:${PATH}"
                }

                // Vérifie que Maven est correctement installé
                sh 'mvn -version'

                // Build le projet Maven
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Exécuter les tests
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                // Déployer l'application
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
