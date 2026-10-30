
pipeline {
    agent any

    environment {
        IMAGE = 'laravel-app:latest'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/maidafayyaz29/laravel_jenkin_lab.git'
            }
        }

        stage('Build') {
            steps {
                sh 'minikube image build -t laravel-app:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'kubectl apply -f k8s/mysql.yaml'
                sh 'kubectl apply -f k8s/laravel.yaml'
            }
        }

        stage('Verify') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get services'
            }
        }
    }
}
