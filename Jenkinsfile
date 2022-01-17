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
           script{
                def mavenPom = readMavenPom file: 'pom.xml'
                def nexusRepoName = mavenPom.version.endsWith("SNAPSHOT") ? "simpleapp-snapshot" : "simpleapp-release"
            
            nexusArtifactUploader artifacts: [
                [
                    artifactId: 'simple-app', 
                    classifier: '', 
                    file: "target/simple-app-${mavenPom.version}.war", 
                    type: 'war'
                    ]
                ], 
                credentialsId: 'cd6fb5cd-0b89-4fa9-8788-330ef50e6edc', 
                groupId: 'in.javahome', 
                nexusUrl: '172.31.3.147:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: nexusRepoName, 
                version: "${mavenPom.version}"
           }
        }
            

        }
    }
}