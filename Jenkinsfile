pipeline {
    agent any
    stages {
        stage('Install') {
            steps {
                withMaven(maven: 'Maven') {
                 sh "mvn clean test"
                }                
            }
        }
        stage('Sonar') {
            steps {
                withSonarQubeEnv(sonar:'Sonar') {
                    echo 'Helo'
                }
            }
        }
    }
}
