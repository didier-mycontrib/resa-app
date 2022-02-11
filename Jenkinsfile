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
			   ws("/conf-docker/frontend-resa/my-frontend-resa/frontend-content") {
				  checkout scm
			   }
			}
		}
		stage('Install') {
            steps { 
			ws("/conf-docker/frontend-resa/my-frontend-resa/frontend-content") {
					sh ('npm install')
				}
			}
        }
		stage('Build') {
			steps {
			   ws("/conf-docker/frontend-resa/my-frontend-resa/frontend-content"){
					sh ('npm run build') 
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
