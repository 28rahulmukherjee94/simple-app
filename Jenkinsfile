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
           stage('Upload war to nexus'){
               def mavenPom = readMavenPom file: 'pom.xml'
            steps{
                
                script{
                    
                    nexusArtifactUploader artifacts: [[artifactId: 'simple-app', classifier: '', file: "target/simple-app-${mavenPom.version}.war", type: 'war']], credentialsId: 'a01f180b-a7f2-481e-bd0e-e1560b51b9f0', groupId: 'in.javahome', nexusUrl: '172.31.10.72:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'simpleapp-release', version: "${mavenPom.version}"
                }
            }


        }
    }
}