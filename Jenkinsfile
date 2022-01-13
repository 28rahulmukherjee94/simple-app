pipeline{
    agent any
    tools {
  maven 'maven3'
}


    stages{
        stage('Build'){
            sh 'mvn clean package'

        }
    }
}