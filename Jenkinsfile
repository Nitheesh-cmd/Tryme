pipeline {
    agent any
   tools {
        maven 'Maven' 
    }
    stages {
       /* stage('Install') {
            steps {
                withMaven(maven: 'Maven') {
                 sh "mvn clean test"
                }                
            }
        }*/
        stage('Sonar') {
            steps {
                withSonarQubeEnv('Sonar') {
                   sh 'mvn install'
                }
                withCredentials([string(credentialsId: 'admin', variable: 'admin')]) {
        sh "${sonarqubeScannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://http://10.204.100.144:9000 -Dsonar.login=${sonarLogin} -Dsonar.projectName=gs-gradle -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=GS -Dsonar.sources=src/main/ -Dsonar.tests=src/test/ -Dsonar.language=java -Dsonar.java.binaries=."
               }
            }
        }
    }
}
