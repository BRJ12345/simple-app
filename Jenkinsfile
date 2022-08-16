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
        }   

        stage('upload war  to nexus') {
            steps{
                script{
                    def mavenPom = readMavenPom file: 'pom.xml'
            nexusArtifactUploader artifacts: [
                [
                    artifactId: 'simple-app',
                    classifier: '', 
                    file: "target/simple-app-${mavenPom.version}.war", 
                    type: 'war'
                ]
            ],  
            credentialsId: 'nexus3', 
            groupId: 'in.javahome', 
            nexusUrl: '172.31.26.224:8081', 
            nexusVersion: 'nexus3', 
            protocol: 'http', 
            repository: 'http://18.234.235.87:8081/repository/simpleapp-release/', 
            version: "${mavenPom.version}"
                }
            }
        }
    }
}

