pipeline {
    agent {label 'slave'}
    tools {
        maven 'Maven'
    }
    stages {
        stage ('SCM checkout') {
            steps {
                git 'https://github.com/Rohana-R/Chat_Room.git'
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
    post {
        always {
            emailext (
                to: 'rohana.r.90@gmail.com',
                subject: 'Build ${BUILD_NUMBER} - ${BUILD_STATUS}',
                body: 'The build has completed with status: ${BUILD_STATUS}',
                attachLog: true
            )
        }
    }
}
