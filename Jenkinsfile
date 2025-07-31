pipeline {
    agent any

    tools {
        maven 'Maven 3.8.5' // Must match Jenkins tool config
    }

    environment {
        SONAR_SCANNER_HOME = tool 'SonarQube Scanner'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Saurav-Kumar-02/devops-practice.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "${env.SONAR_SCANNER_HOME}/bin/sonar-scanner \
                        -Dsonar.projectKey=devops-practice \
                        -Dsonar.sources=. \
                        -Dsonar.java.binaries=target"
                }
            }
        }

        stage("Quality Gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
