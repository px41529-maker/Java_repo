pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/px41529-maker/Java_repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                deploy adapters: [
                    tomcat10(
                        credentialsId: 'tomcat-creds',
                        url: 'http://SERVER-IP:8080'
                    )
                ],
                war: 'target/*.war'
            }
        }
    }
}
