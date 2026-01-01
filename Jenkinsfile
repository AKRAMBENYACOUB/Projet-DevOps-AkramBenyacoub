pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/AKRAMBENYACOUB/Projet-DevOps-AkramBenyacoub.git'
            }
        }

        stage('Build & Test') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw -f hello-devops/pom.xml clean test package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'hello-devops/target/*.jar'
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS'
        }
        failure {
            echo 'Pipeline FAILED'
        }
    }
}
