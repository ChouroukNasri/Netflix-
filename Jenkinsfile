pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker')
    }
    stages {
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build("yourdockerhubusername/netflix")
                }
            }
        }
        stage('Push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker') {
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
