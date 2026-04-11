def utils

pipeline {   
    agent any

    stages {
        stage ("__init__"){
            steps{
                script{
                    utils = load "utils.groovy"
                    utils.say_hello()
                    env.TEST_VAL = "42"
                }
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
                    sh 'env'
                    echo "###############################"
                    echo "$TEST_VAL $TEST_VAL $TEST_VAL"
                }                    
            }
        }       
    }
} 

