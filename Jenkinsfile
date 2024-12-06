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
 script {deploy adapters: [tomcat9(credentialsId: '4ac920ee-efa7-407f-85ac-76adef4a8077', path: '', url: 'https://localhost:8080/')], contextPath: '/CI-CD', war: '**/*.war'}
 }
 }
 }
}
