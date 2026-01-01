pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'Maven'
    }

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
            when {
                expression { currentBuild.currentResult == 'SUCCESS' }
            }
            steps {
                archiveArtifacts artifacts: 'hello-devops/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline SUCCESS'
        }
        failure {
            echo '❌ Pipeline FAILED'
        }
    }
}
