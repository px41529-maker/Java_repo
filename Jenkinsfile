pipeline {
    agent any

    stages {

        stage('Verify Environment') {
            steps {
                sh '''
                java -version
                mvn -version
                pwd
                ls -la
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build Successful'
        }

        failure {
            echo 'Build Failed'
        }
    }
}
