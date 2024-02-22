pipeline {
    agent any

    environment {
        registry = "ranimmbarek/DevopsLab" 
    }

    stages {
        stage('Pull from GitHub') {
            steps {
                git 'https://github.com/farahsedd/DevOps-Lab'
            }
        }

        stage('Build Docker image') {
            steps {
                script {
                    docker.build("${registry}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                // Push the Docker image to DockerHub
                script {
                    docker.withRegistry('') {
                        docker.image("${registry}:${BUILD_NUMBER}").push('latest')
                    }
                }
            }
        }
    }
}