pipeline {
    agent any
    //tools {
    //    maven 'maven'  // Ensure this matches the Maven tool name configured in Jenkins
    //}
    stages {
        stage("Git checkout") {
            steps {
                git 'https://github.com/sten-benny/Maven-Web-Project.git'
            }
        }
        stage("Unit test") {
            steps {
                script {
                sh 'mvn test'
                }
            }
        }
        stage("Maven build") {
            steps {
                script{
                    sh 'mvn clean install'
                }
            }
        }
    }
}
