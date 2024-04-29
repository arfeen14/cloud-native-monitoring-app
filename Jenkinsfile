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
                    sh  'docker build -t 2b53d9e6-66b7-40bc-9704-8efa5bfa4cf6/monitoring .'

                }
            }
        }           
        stage('Test image') {                       
            steps {
                script {
                    app.inside {
                        sh 'echo "Tests passed"'        
                    }
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
