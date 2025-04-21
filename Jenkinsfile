pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage('git checkout') {
            steps {
                git 'https://github.com/Rohana-R/Chat_Room.git'
            }
        }
        stage('code analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Chat_Room \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=Chat_Room'''
                   }
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
                    sh 'docker run -itd --name chat-cont -p 8084:8080 rohana1234/chat-room'
                }
            }
        }
    }
}
