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
deploy adapters: [tomcat9(credentialsId: '7346dd20-b459-4eaf-971b-808ea3a459ff', path: '', url: 'http://localhost:8080/')], contextPath: '/ci-cd-jk', war: '**/*.war' }
 }
 }
 }
}

