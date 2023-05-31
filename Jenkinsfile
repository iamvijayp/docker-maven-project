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
        stage('Build And Push Docker Image'){
            agent any
            environment{
            registry = "iamvijayp/myapp"
            }
            steps{
                script{
                docker.withRegistry('https://index.docker.io/v1/', 'docker-cred') {
                docker.build("$registry" +":$BUILD_NUMBER").push()
                    }
                }
            }
        }
    }
}