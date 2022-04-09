pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
            }
        }
        stage('Upload War To Nexus'){
            steps{
                 nexusArtifactUploader artifacts: [
                     [
                         artifactId: 'simple-app', 
                         classifier: '', 
                         file: 'target/simple-app-3.0.0-SNAPSHOT.war', 
                         type: 'war'
                    ]
                ], 
                credentialsId: 'nexus-creds', 
                groupId: 'in.javahome', 
                nexusUrl: '192.168.1.7:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'maven-central-repo', 
                version: '3.0.0-SNAPSHOT'
            }
        }
    }
}
