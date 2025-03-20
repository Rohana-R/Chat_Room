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
                sh 'mvn compile'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
