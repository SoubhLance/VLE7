pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Docker Test') {
            steps {
                sh 'docker --version'
                sh 'docker ps'
            }
        }
    }
}
