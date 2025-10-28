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
                withSonarQubeEnv('MyLocalSonarQube') { // Name must match Jenkins configuration
                    sh 'sonar-scanner'
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
