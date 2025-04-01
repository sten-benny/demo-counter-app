pipeline {
    agent any
    //tools {
    //    maven 'maven'  // Ensure this matches the Maven tool name configured in Jenkins
    //}
    stages {
        stage("Git checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/sten-benny/demo-counter-app.git'
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
