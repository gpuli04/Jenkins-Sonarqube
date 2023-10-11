pipeline {
    agent any

    environment {
        SONARQUBE_SERVER = 'http://3.108.67.252:9000' // Your SonarQube server URL
        SONARQUBE_TOKEN = credentials('2b993139-f9a6-4932-b7b2-c1ff09ed062d') // Use the Sonarqube credentials ID
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out the GitHub repository
                checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/gpuli04/Jenkins-Sonarqube.git']])
            }
        }

        stage('Build and Test') {
            steps {
                script {
                    // Build the project (You may need to adjust the build command)
                    sh 'msbuild YourSolution.sln'

                    // Run the unit tests (You may need to adjust the test command)
                    sh 'nunit YourTestProject.dll'

                    // Generate a test report (if applicable)
                    // nunit-console --result:TestResult.xml

                    // Perform SonarQube code scanning
                    withSonarQubeEnv('SonarQube') {
                        sh "sonar-scanner -Dsonar.login=${SONARQUBE_TOKEN} -Dsonar.host.url=${SONARQUBE_SERVER}"
                    }
                }
            }
        }
    }
}
