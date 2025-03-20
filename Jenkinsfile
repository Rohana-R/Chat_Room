pipeline {
    agent {label 'windows-slave'}
    tools {
    maven 'Maven'
    }
    stages {
        stage('git checkout') {
            steps {
                git 'https://github.com/Rohana-R/Chat_Room.git'
            }
        }
        stage('compile') {
            steps {
                bat 'mvn compile'
            }
        }
        stage('build') {
            steps {
                bat 'mvn package'
            }
        }
    }
}
