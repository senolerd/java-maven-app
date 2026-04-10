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
            environment {
                MY_CREDS = credentials('aws-cred-admin')
            }

            steps{
                echo "AWS CLI VERSION"
                sh 'AWS_SECRET_ACCESS_KEY=$MY_CREDS_PSW'
                sh 'AWS_ACCESS_KEY_ID=$MY_CREDS_USR'
                // withCredentials([usernamePassword(credentialsId: 'aws-cred-admin', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {  }
                // export AWS_ACCESS_KEY_ID=$MY_CREDS_USR
                // export AWS_SECRET_ACCESS_KEY=MY_CREDS_PSW
                // echo AWS_ACCESS_KEY_ID = $MY_CREDS_USR
                sh 'env'
                // sh 'aws s3 ls'                    
                

            }
        }       
    }
} 
