pipeline {
    agent any
    
    stages {
        stage('Clone repository') {               
            steps {
                script {
                    checkout scm    
                }
            }
        }           
        stage('Build image') {         
            steps {
                script {
                    sh  'docker build -t dockerhub_credentials/monitoring .'

                }
            }
        }           
        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'git') {
                        app.push("${env.BUILD_NUMBER}")            
                        app.push("latest")        
                    }
                }
            }
        }
    }
}
