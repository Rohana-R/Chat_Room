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
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Chat-Room \
                    -Dsonar-projectKey=Chat_Room
                    }
           }
          } 
        stage('docker build') {
            steps {
                script {
                    sh 'docker build -t chat-room .'
                }
            }
        }
        stage('docker push') {
            steps {
                script {
                    sh 'docker push chat-room'
                }
            }
        }
        stage('docker container') {
            steps {
                script {
                    sh 'docker run -itd --name chatroom-cont -p 8084:8080 chat-room'
                }
            }
        }
    }
}
