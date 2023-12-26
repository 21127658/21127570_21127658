/* Requires the Docker Pipeline plugin */
pipeline {
    agent any
    environment {
        dockerImage = ''
        registry = '21127658/21127570_21127658'
        registryCredential = 'Docker'
    }
    stages {
        stage('Checkout'){
            steps {
                checkout scm
            }
        }
        stage('Hello world') {
            steps {
                echo 'Hello world!' 
            }
        }
        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build registry
                }
            }
        }
        stage('Uploading Image') {
            steps {
                script {
                    docker.withRegistry( '', registryCredential){
                        dockerImage.push()
                    }
                }
            }
        }
        stage('Docker Run') {
        steps{
            script {
                dockerImage.run("-p 8096:5000 --rm --name 21127570_21127658")
            }
        }
        }
    }
}
