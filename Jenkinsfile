pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "23mis0251/springboot-app:latest"
    }

    stages {

        stage('Clone') {
            steps {
                git url: 'https://github.com/your-repo-link.git', branch: 'main'
            }
        }

        stage('Build Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t %DOCKER_IMAGE% .'
            }
        }

        stage('Push Docker') {
            steps {
                bat 'docker push %DOCKER_IMAGE%'
            }
        }

        stage('Deploy Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
            }
        }
    }
}