pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hier gaan we de docker file builden: docker build .'
                "sh docker build -t arfeenalam/devops_repo . "
            }
        }
        stage('Deploy') {
            steps {
                echo 'niet vergeten maak een script die automatisch de nieuwe image runtg lokaal op je pc.'

              }    
            }
        }
    }
