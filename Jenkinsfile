pipeline {
    agent {
        docker {
            image 'maven:3.9.0-eclipse-temurin-11'
            // args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
            sh 'mvn -B -DskipTests clean package' //this command will be executed inside maven container
            }
        }
    }
}