pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('MySonarServer') {
                    sh 'mvn clean verify sonar:sonar'
                }
            }
        }
    }
}
