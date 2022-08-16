pipeline {
    agent any
    tools {
      maven 'maven3'
    }
    stages {
        stage('build') {
            sh 'mvn clean package'
        }
    }
}
