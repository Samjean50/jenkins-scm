pipeline {
    agent any

    stages {
        stage('Connect To Github') {
            steps {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Samjean50/jenkins-scm.git']])
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t dockerfile .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -itd --name nginx -p 8081:80 dockerfile'
                }
            }
        }
    }
}
