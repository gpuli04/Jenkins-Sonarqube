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
stage('Build') {
steps {
dir('samplecode') {
sh 'msbuild YourSolution.sln'
}
}
}
stage('Test') {
steps {
dir('samplecode') {
sh 'nunit YourTestProject.dll'
}
}
}
stage('Test Reporting') {
steps {
dir('samplecode') {
junit 'TestResult.xml'
}
}
}
stage('Code Scan') {
steps {
dir('samplecode') {
script {
withSonarQubeEnv('SonarQube') {
sh "sonar-scanner -Dsonar.login=${SONARQUBE_TOKEN} -Dsonar.host.url=${SONARQUBE_SERVER}"
}
}
}
}
}
}

post {
always {
// Clean up and other post-build tasks
}
}
}
