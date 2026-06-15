pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/px41529-maker/Java_repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

       stage('Deploy') {
    steps {
        sh '''
        sudo cp target/ROOT.war /opt/tomcat/webapps/ROOT.war
        '''
    }
}
    }
}
