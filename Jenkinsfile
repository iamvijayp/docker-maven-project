pipeline {
    agent none
    stages {
        stage('Maven Build') {
            agent {
            docker { 
                image 'maven:3.9.0-eclipse-temurin-11'
            // args '-v $HOME/.m2:/root/.m2'
            }
            }
            steps {
            sh 'mvn -B -DskipTests clean package' //this command will be executed inside maven container
            }
        }
        stage('Build Docker Image'){
            agent any
        steps{
            sh 'pwd'
            sh 'ls -la webapp/target/webapp.war'
            sh 'docker build -t sample-image .'
        }
        }
        stage('Docker Image Copy'){
        steps{
            sh 'echo Docker Image Copy'
            //comment
        }
        }
    }
}