pipeline {
    agent any
   tools {
        maven 'Maven' 
    }
    stages {
        stage('Install') {
            steps {
                 withSonarQubeEnv('Sonar') {
                   sh 'mvn install'
                }            
            }
        }
        stage('Sonar') {
            steps {
                script{
          sonarqubeScannerHome = tool name: 'Sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                }
                withCredentials([string(credentialsId: 'Sonar', variable: 'sonarLogin')]) {
        sh "${sonarqubeScannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=${sonarLogin} -Dsonar.projectName=Sonar-Test -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=Test -Dsonar.sources=src/main/ -Dsonar.tests=src/test/ -Dsonar.language=java -Dsonar.java.binaries=."
               }
            }
        }
    }
}
