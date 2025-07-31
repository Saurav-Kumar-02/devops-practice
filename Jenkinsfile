pipeline {
    agent any

    tools {
        maven 'Maven 3.9.6'  // Ensure this is configured in Jenkins tools
    }

    environment {
        SONARQUBE_ENV = 'SonarQube' // This must match Jenkins config name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Saurav-Kumar-02/devops-practice.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_ENV}") {
                    dir('devops-practice') { // 👈 THIS is the key fix
                        sh 'mvn clean verify sonar:sonar'
                    }
                }
            }
        }
    }
}
