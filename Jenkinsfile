pipeline {
    agent any
    
    environment {
        DOCKER_ID = credentials('dockerhub_id')
        DOCKER_PASSWORD = credentials('dockerhub_credentials')
    }

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
                    sh  'docker build -t $DOCKER_ID/devops_repo:latest .'

                }
            }
        }           
        stage('Push image') {
            steps {
                script {
                        echo 'hier loggen we eerts in met de dockerHub credentials'
                        sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_ID --password-stdin'
                        echo 'hier pushen we het naar de juiste dockerhub repository met een tag(zoals in de docu beschreven)'
                        sh 'docker image ls'
                        sh 'docker push $DOCKER_ID/devops_repo:latest'    
                    }
                }
            }
        }
    }

