pipeline {
    agent none
    stages {
        stage('Maven Build') {
            agent {
                docker { 
                    image 'maven:3.9.0-eclipse-temurin-11'
                }
            }
            steps {
            sh 'mvn -B -DskipTests clean package' //this command will be executed inside maven container
            }
        }
        stage('Test')
        {
            agent any
            steps{
                sh '''ls -lrt
                pwd
                '''
            }
        }
        stage('Build And Push Docker Image'){
            agent any
        steps{
            script{
            docker.withRegistry('https://hub.docker.com/', 'docker-cred') {
            docker.build("iamvijayp/myapp" +":$BUILD_NUMBER").push()
        }
        }
        }
        }
    }
}