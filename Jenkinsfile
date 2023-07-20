pipeline {
 environment {
 imagename = “rahmatmustaqim69/jenkins-docker”
 registryCredential = ‘rahmatmustaqim69’
 dockerImage = ‘’
 }
 agent any
 stages {
 stage(‘Cloning Git’) {
 steps {
 git([url: ‘https://github.com/rahmatmustaqim69/simple-docker.git’, branch: ‘main’])
 }
 }
 stage(‘Building image’) {
 steps{
 script {
 dockerImage = docker.build imagename
 }
 }
 }
 stage(‘Running image’) {
 steps{
 script {
 sh “docker run ${imagename}:latest”
 }
 }
 }
 stage(‘Deploy Image’) {
 steps{
 script {
 docker.withRegistry( ‘’, registryCredential ) {
 dockerImage.push(“$BUILD_NUMBER”)
 dockerImage.push(‘latest’)
 }
 }
 }
 }
 }
}
