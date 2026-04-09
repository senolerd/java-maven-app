// def gv

pipeline {   
    agent any
    stages {
        stage("build jar") {
            agent {
                docker {
                    image 'docker.io/maven'
                    // image 'docker.io/maven:3-eclipse-temurin-17'
                    reuseNode true
                    args '--userns=keep-id --entrypoint=""'
                }
            }
            steps {
                // sh 'mvn package'
                echo "Building in MAVEN container"
            }
        }
        stage("AWS Cki for uploading image"){
            agent { 
                docker { 
                    image 'docker.io/amazon/aws-cli' 
                    args '--userns=keep-id --entrypoint=""'
                    reuseNode true
                }
            }

            steps{
                echo "AWS CLI VERSION"
                sh 'aws --version'                

            }
        }       
    }
} 
