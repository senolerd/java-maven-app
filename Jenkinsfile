def mylib

pipeline {   
    agent any

    stages {
        stage ("__init__"){
            steps{
                mylib = load 'utils.groovy'
                mylib.say_hello(j)
            }
        }

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
            environment {
                MY_CREDS = credentials('aws-cred-admin')
            }

            steps{
                script {
                    echo "AWS CLI VERSION"
                    withCredentials( [usernamePassword(credentialsId: 'aws-cred-admin', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID') ] ) {  
                        sh 'aws s3 ls'
                    }
                }                    
            }
        }       
    }
} 
