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
                script {
          // requires SonarQube Scanner 2.8+
          sonarqubeScannerHome = tool name: 'Sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                      }
                withSonarQubeEnv('Sonar') {
                   sh 'mvn install'
                }
                withCredentials([string(credentialsId: 'Sonar', variable: 'sonarLogin')]) {
        sh "${sonarqubeScannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=${sonarLogin} -Dsonar.projectName=Sonar-Test -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=Test -Dsonar.sources=src/main/ -Dsonar.tests=src/test/ -Dsonar.language=java -Dsonar.java.binaries=."
               }
            }
        }
    }
}
