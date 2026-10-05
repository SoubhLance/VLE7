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

        stage('Docker Build') {
            steps {
                sh 'docker build -t vle7-app:latest .'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker rm -f vle7-container || true'
                sh 'docker run -d --name vle7-container -p 8080:8080 vle7-app:latest'
            }
        }

        stage('Docker Verify') {
            steps {
                sh 'docker ps'
                sh 'docker logs --tail 20 vle7-container'
            }
        }
    }
}
