// def gv

pipeline {   
    agent any
    // tools {
    //     maven 'mAVEN-3.9.14'
    // }
    stages {
        // stage("init") {
        //     steps {
        //         script {
        //             gv = load "script.groovy"
        //         }
        //     }
        // }
        stage("build jar") {
            agent {
                docker {
                    image 'docker.io/maven'
                    reuseNode true
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

        // stage("build image") {
        //     steps {
        //         script {
        //             gv.buildImage()
        //         }
        //     }
        // }

        // stage("deploy") {
        //     steps {
        //         script {
        //             gv.deployApp()
        //         }
        //     }
        // }               
    }
} 
