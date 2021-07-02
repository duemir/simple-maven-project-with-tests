pipeline {
    agent {
        kubernetes {
            defaultContainer 'maven'
            yaml '''\
apiVersion: v1
kind: Pod
spec:
    containers:
    - name: maven
      image: maven
      command:
      - sleep
      arguments:
      - infinity
'''
        }
    }
    stages {
        stage('Verify') {
            sh 'mvn -B -ntp -Dmaven.test.failure.ignore verify'
            junit '**/target/surefire-reports/TEST-*.xml'
        }
    }
}

