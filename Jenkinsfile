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
                   sh 'mvn clean test'
                }
            }
        }
    }
}
