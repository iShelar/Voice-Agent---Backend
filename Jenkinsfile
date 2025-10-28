pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/iShelar/Voice-Agent---Backend.git', branch: 'main'
            }
        }
        def scannerHome = tool 'SonarQubeScanner'
        stage('SonarQube Code Analysis') {
            steps {
                withSonarQubeEnv('Local Voice Agent Config') { // Name must match Jenkins configuration
                    sh "${scannerHome}/bin/sonar-scanner"
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
