pipeline{
    agent any
    tools {
  maven 'maven3'
}


    stages{
        stage('Build'){
        steps{
            sh 'mvn clean package'
        }
            

        }
         stage('Upload War to nexus'){
        steps{
            
            nexusArtifactUploader artifacts: [
                [
                    artifactId: 'simple-app', 
                    classifier: '', 
                    file: 'target/simple-app-1.0.0.war', 
                    type: 'war'
                    ]
                ], 
                credentialsId: 'cd6fb5cd-0b89-4fa9-8788-330ef50e6edc', 
                groupId: 'in.javahome', 
                nexusUrl: '172.31.3.147:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'simpleapp-release', 
                version: '1.0.0'
        }
            

        }
    }
}