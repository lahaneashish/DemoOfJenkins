pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "your-dockerhub-username/hello-word"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/YOUR-USERNAME/YOUR-REPO.git'
            }
        }

        stage('Build JAR') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                echo "Skipping push for now"
                // later we will add credentials
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yml'
                sh 'kubectl apply -f service.yml'
            }
        }
    }
}