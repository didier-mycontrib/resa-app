pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from resa-app'
            }
		}
		stage('Checkout code') {
			steps {
			   ws("/conf-docker/frontend-resa/my-frontend-resa") {
				  checkout scm
			   }
			}
		}
		stage('recompose docker container') {
			steps {
			    ws("/conf-docker/frontend-resa") {
				     sh('date > lastUpdate.txt')
				}
			}
		}
    }
}
