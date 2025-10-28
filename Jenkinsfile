pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/iShelar/Voice-Agent---Backend.git', branch: 'main'
            }
        }
        stage('SonarQube Code Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarQubeScanner'
                    withSonarQubeEnv('SonarQube') {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t voice-agent .'
            }
        }
        stage('Unit Test (optional)') {
            steps {
                sh 'echo "No tests defined yet!"'
            }
        }
        stage('Finish') {
            steps {
                echo 'Pipeline complete!'
            }
        }
    }
}
