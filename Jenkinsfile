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
  //      stage("Static code analaysis") {
  //          steps {
  //              script{
   //                 withSonarQubeEnv(credentialsId: 'sonarid') {
   //                 sh 'mvn clean package sonar:sonar'
   //                 }
   //             }
//         }
  //      }
//       stage("Quality Gate") {
//            steps {
 //               script {
 //               waitForQualityGate abortPipeline: false, credentialsId: 'sonarid'
  //              }
   //         }
   //     }      
        stage("Upload file to nexus") {
            steps {
                script {
                    def readPomversion = readMavenPom file :'pom.xml'
                    def nexusRepo = readPomversion.version.endsWith("SNAPSHOT") ? "demoapp-snapshot" : "demoapp-release"
                nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/Uber.jar', type: 'jar']], 
                    credentialsId: 'nexus-auth', 
                    groupId: 'com.example', 
                    nexusUrl: '34.202.166.173:8081', 
                    nexusVersion: 'nexus3',
                    protocol: 'http', 
                    repository: nexusRepo, 
                    version: "${readPomversion.version}"
                }
            }
        }
    }
}
