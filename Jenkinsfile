pipeline {
environment {
dockerImage = ''
}
    agent any

    stages {
        stage('Cloning our Git') {
            steps {
                script {
                    git 'https://github.com/arfeen14/cloud-native-monitoring-app.git'
                }
            }
        }
        stage('Building our image') {
            steps {
                dockerImage = docker.build registry + ":$BUILD_NUMBER"
            }
        }
        stage('Deploy our image') {
            steps {
                script {
                    docker.withRegistry( '', '2b53d9e6-66b7-40bc-9704-8efa5bfa4cf6' ) {
                    dockerImage.push()
                }
            }
        }
    }
}