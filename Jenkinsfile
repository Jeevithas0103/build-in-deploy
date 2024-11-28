pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '457c6557-e99a-4202-a54e-7403bd8d5340', path: '', url: 'http://localhost:8080')], contextPath: '/ci-cd-jk', war: '**/*.war'}
 }
 }
 }
}
