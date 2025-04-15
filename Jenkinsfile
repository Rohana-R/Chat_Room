pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git 'https://github.com/Rohana-R/Chat_Room.git'
            }
        }
        stage('docker build') {
            steps {
                script {
                    sh 'docker build -t rohana1234/chat-room .'
                }
            }
        }
        stage('docker push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                    sh 'docker push rohana1234/chat-room'
                    }
                }
            }
        }
        stage('docker container') {
            steps {
                script {
                    sh 'docker run -itd --name chat-cont -p 8082:8080 rohana1234/chat-room'
                }
            }
        }
    }
}
