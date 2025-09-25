pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('bharani7d')
    }
    stages {
        stage('Test Credentials') {
            steps {
                echo "DockerHub user is $DOCKERHUB_CREDENTIALS_USR"
            }
        }
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t week7-pipeline .'
            }
        }
        stage('Push to DockerHub') {
            steps {
                sh """
                  docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW
                  docker tag week7-pipeline bharani7d/week7-pipeline:v1
                  docker push bharani7d/week7-pipeline:v1
                """
            }
        }
    }
}
