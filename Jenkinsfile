pipeline {
    agent any

    environment {
        SONARQUBE_SERVER = 'http://3.108.67.252:9000' // Your SonarQube server URL
        SONARQUBE_TOKEN = credentials('2b993139-f9a6-4932-b7b2-c1ff09ed062d') // Use the Sonarqube credentials ID
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/gpuli04/Jenkins-Sonarqube.git']])
                }
            }
        }

        // Rest of your stages...

    }

    post {
        always {
            // Clean up and other post-build tasks
        }
    }
}
