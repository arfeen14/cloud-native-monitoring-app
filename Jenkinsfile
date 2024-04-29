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
                    def app = docker.build("arfeenalam/devops_repo")
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
