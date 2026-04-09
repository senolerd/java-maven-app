// def gv

pipeline {   
    agent any
    stages {
        stage("build jar") {
            agent {
                docker {
                    // image 'docker.io/maven'
                    image 'docker.io/maven:3-eclipse-temurin-17'
                    // reuseNode true
                    args '--userns=keep-id --entrypoint=""'
                }
            }
            steps {
                sh 'mvn package'
                // script {
                //     // gv.buildJar()
                //     sh "echo HELLO"
                //     sh "mvn package"
                // }
            }
        }           
    }
} 
