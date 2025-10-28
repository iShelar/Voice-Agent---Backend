pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'docker'
        DOCKERHUB_USERNAME = 'ishelar'
        IMAGE_NAME = 'voice-agent'
    }

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
                sh "docker build -t ${IMAGE_NAME}:latest ."
                sh "docker tag ${IMAGE_NAME}:latest ${DOCKERHUB_USERNAME}/${IMAGE_NAME}:latest"
            }
        }
        stage('Docker Hub Login & Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: "${DOCKERHUB_CREDENTIALS}", usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin'
                    sh "docker push ${DOCKERHUB_USERNAME}/${IMAGE_NAME}:latest"
                }
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
