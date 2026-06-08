pipeline {
agent any

```
stages {

    stage('Checkout Code') {
        steps {
            git branch: 'dependabot/maven/junit-junit-4.13.1',
                url: 'https://github.com/SyedGilman/simpleMavenJunit.git'
        }
    }

    stage('Maven Clean') {
        steps {
            sh 'mvn clean'
        }
    }

    stage('Maven Compile') {
        steps {
            sh 'mvn compile'
        }
    }

    stage('Maven Test') {
        steps {
            sh 'mvn test'
        }
    }

    stage('Maven Package') {
        steps {
            sh 'mvn package'
        }
    }
}

post {
    always {
        junit allowEmptyResults: true,
              testResults: '**/target/surefire-reports/*.xml'
    }

    success {
        archiveArtifacts artifacts: 'target/*.jar',
                         fingerprint: true
    }
}
```

}
