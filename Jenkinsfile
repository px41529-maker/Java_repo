pipeline {
agent any

```
stages {

    stage('Checkout') {
        steps {
            checkout scm
        }
    }

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

    stage('Verify WAR Generated') {
        steps {
            sh '''
            ls -lh target/*.war
            '''
        }
    }

    stage('Deploy to Tomcat') {
        steps {
            sh '''
            sudo cp target/*.war /var/lib/tomcat10/webapps/
            '''
        }
    }

    stage('Verify Deployment') {
        steps {
            sh '''
            sleep 20
            ls -lh /var/lib/tomcat10/webapps/
            curl -I http://localhost:8080
            '''
        }
    }
}

post {
    success {
        echo 'Application deployed successfully to Tomcat'
    }

    failure {
        echo 'Build or Deployment Failed'
    }
}
```

}
