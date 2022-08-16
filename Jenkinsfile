pipeline {
    agent any
    tools {
      maven 'maven3'
    }
    stages {
        stage('build') {
            steps{
            sh 'mvn clean package'
            }

        stage('upload war  to nexus') {
            steps{
            nexusArtifactUploader artifacts: [
                [
                    artifactId: 'simple-app',
                    classifier: '', 
                    file: 'target/simple-app-1.0.0.war', 
                    type: 'war'
                ]
            ], 
            credentialsId: 'nexus3', 
            groupId: 'in.javahome', 
            nexusUrl: '172.31.26.224:8081', 
            nexusVersion: 'nexus3', 
            protocol: 'http', 
            repository: 'http://18.234.235.87:8081/repository/simpleapp-release/', 
            version: '1.0.0'
            }
        }
    }
}
}
