pipeline {
    agent any
    
    environment {
        SONAR_QUBE_HOME = tool 'SonarQubeScanner'
        GITHUB_REPO_URL = 'https://github.com/AlexMicheal50/Jenkins_SonarQube_Docker.git'
    }
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the code from the GitHub repository
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: "${GITHUB_REPO_URL}"]]])
                }
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarQubeScanner'
                    withSonarQubeEnv() {
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.login=sqa_1c8949b2f73098e43bac0995674690e5dd44a36a -Dsonar.projectKey=test-project"
                    }
                }
            }
        }
    }
}
