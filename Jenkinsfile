pipeline {
    agent any

    stages {

        stage('Verify Environment') {
            steps {
                sh '''
                java -version
                mvn -version
                '''
            }
        }

        stage('Build WAR') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Verify Artifact') {
            steps {
                sh 'ls -lh target/'
            }
        }

        stage('Archive WAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'WAR Build Successful'
        }

        failure {
            echo 'WAR Build Failed'
        }
    }
}
