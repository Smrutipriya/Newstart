pipeline {
    agent any
    stages{
        stage('Build'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Smrutipriya/Newstart']]])
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t smrutipriya/httpbin .'
                }
            }
        }
        stage('push image to dockerhub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'Dockerhub', variable: 'dockerhub')]) {
                    sh 'docker login -u smrutipriya -p ${dockerhub}'
}
                    sh 'docker push smrutipriya/httpbin'
                }
            }
        }
    }
}