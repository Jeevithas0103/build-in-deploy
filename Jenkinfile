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
deploy adapters: [tomcat9(credentialsId: '08caea2b-515d-4fb1-ade7-3264f7df5e24', path: '', url: 'http://localhost:8080')], contextPath: '/ci-cd-jk', war: '**/*.war'}
 }
 }
 }
}
