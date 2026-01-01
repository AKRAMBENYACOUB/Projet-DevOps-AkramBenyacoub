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
                dir('hello-devops') {
                    sh 'mvn clean test package'
                }
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
            slackSend(
                channel: '#jenkins-devops',
                message: "✅ SUCCESS : Pipeline DevOps AkramBenyacoub\n${env.BUILD_URL}"
            )
        }
        failure {
            slackSend(
                channel: '#jenkins-devops',
                message: "❌ FAILURE : Pipeline DevOps AkramBenyacoub\n${env.BUILD_URL}"
            )
        }
    }
}

