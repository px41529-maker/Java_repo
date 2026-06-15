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

    stage('Verify WAR') {
        steps {
            sh 'ls -lh target/*.war'
        }
    }

    stage('Deploy to Tomcat') {
        steps {
            sh '''
            sudo cp target/*.war /var/lib/tomcat10/webapps/
            '''
        }
    }
}

post {
    success {
        echo 'WAR deployed successfully to Tomcat'
    }

    failure {
        echo 'Build or Deployment Failed'
    }
}
```

}
