pipeline {
    agent any

    stages {
        stage('Build our image') {
            steps {
                echo 'Hier gaan we de docker file builden: docker build .'
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Deploy image to hub') {
            steps {
                echo 'niet vergeten maak een script die automatisch de nieuwe image runtg lokaal op je pc.'
                script {
                docker.withRegistry( '', registryCredential ) {
                dockerImage.push()
                    }
                }
              }    
            }
        }
    }
