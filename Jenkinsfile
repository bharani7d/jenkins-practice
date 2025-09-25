pipeline {
    agent any
    environment {
        DOCKERHUB_USER = credentials('dockerhub-user') // Jenkins credential ID
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: https://github.com/bharani7d/git-week7-practice.git
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${DOCKERHUB_USER}/week7day2:latest .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([ credentialsId: 'dockerhub-user', url: '' ]) {
                    sh 'docker push ${DOCKERHUB_USER}/week7day2:latest'
                }
            }
        }
    }
}
