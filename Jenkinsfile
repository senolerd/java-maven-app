// def gv

pipeline {   
    agent any
    stages {
        stage("build jar") {
            agent {
                docker {
                    // image 'docker.io/maven'
                    image 'maven:3-eclipse-temurin-17'
                    // reuseNode true
                    args '--entrypoint=""'
                }
            }
            steps {
                script {
                    // gv.buildJar()
                    sh "echo HELLO"
                    sh "mvn package"
                }
            }
        }           
    }
} 
