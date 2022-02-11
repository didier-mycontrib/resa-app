pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'resa-app with dist/resa-app already built in this V1'
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
					echo 'npm install may takes too much time ...'
					sh ('npm --version')
				}
			}
        }
		stage('Build') {
			steps {
			   ws("/conf-docker/frontend-resa/my-frontend-resa/frontend-content"){
					echo 'npm run build may takes too much time ...'
					sh ('node --version') 
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
