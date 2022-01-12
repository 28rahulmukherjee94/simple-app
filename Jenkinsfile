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
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'simple-app', classifier: '', file: 'target/simple-app-3.0.0.war', type: 'war']], credentialsId: 'a01f180b-a7f2-481e-bd0e-e1560b51b9f0', groupId: 'in.javahome', nexusUrl: '172.31.10.72', nexusVersion: 'nexus3', protocol: 'http', repository: 'simpleapp-release', version: '3.0.0'
            }


        }
    }
}