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
                    sh 'docker build -t chatroom .'
                }
            }
        }
        stage('dcoker container') {
            steps {
                script {
                    sh 'docker run -itd --name chat1-cont -p 8084:8080 chatroom'
                }
            }
        }
    }
}
