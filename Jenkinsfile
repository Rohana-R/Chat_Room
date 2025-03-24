pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage ('SCM checkout') {
            steps {
                git credentialsId: 'Rohana-R/multi-ssh', url: 'git@github.com:Rohana-R/Chat_Room.git'
            }
        }
        stage ('compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage ('package') {
            steps {
                sh 'mvn package'
            }
        }
    
    }
}
