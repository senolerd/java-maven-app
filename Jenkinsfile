// def gv

pipeline {   
    agent any
    stages {
        stage("build jar") {
            agent {
                docker {
                    image 'docker.io/maven'
                    reuseNode true
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
