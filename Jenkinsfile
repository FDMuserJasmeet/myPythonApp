pipeline {
    agent any
    stages {
        stage('jasmeet.singh - Build docker image') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-pat', url: 'https://github.com/FDMuserJasmeet/myPythonApp.git']])
                    sh "docker build -t jasmeetsingh121125/new-py-image:latest ."
                }
            }
        }
        stage('jasmeet.singh - Login to Dockerhub') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'dockerhub-password', variable: 'dockerhubPwd')]) {
                        sh "docker login -u jasmeetsingh121125 -p ${dockerhubPwd}"
                    }
                }
            }
        }
        stage('jasmeet.singh - Push image to Dockerhub') {
            steps {
                script {
                    sh "docker push jasmeetsingh121125/new-py-image:latest"
                }
            }
        }
    }
}