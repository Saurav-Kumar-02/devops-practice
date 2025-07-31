pipeline {
    agent any

    tools {
        maven 'Maven 3.9.6'  // Set this in Jenkins Global Tool Configuration
    }

    environment {
        SONARQUBE_ENV = 'SonarQube' // Name used in Jenkins SonarQube config
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Saurav-Kumar-02/devops-practice.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_ENV}") {
                    sh 'mvn clean verify sonar:sonar'
                }
            }
        }
    }
}
