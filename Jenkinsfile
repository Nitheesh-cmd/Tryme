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
                sh "mvn sonar:sonar -Dsonar.host.url=${env.SONARQUBE_HOST}"
            }
        }
    }
}
