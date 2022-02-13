pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'resa-app with dist/resa-app already built in this V1 '
            }
		}
		stage('Checkout code') {
			steps {
			   ws("/conf-docker/frontends-angular/my-frontends/resa-app") {
				  checkout scm
			   }
			}
		}
		stage('Install') {
            steps { 
			ws("/conf-docker/frontends-angular/my-frontends/resa-app") {
					echo 'npm install may takes too much time ...'
					sh ('npm --version')
				}
			}
        }
		stage('Build') {
			steps {
			   ws("/conf-docker/frontends-angular/my-frontends/resa-app"){
					echo 'npm run build may takes too much time ...'
					sh ('node --version') 
				}
			}
		}
		stage('copy resa-app from ./resa-app/dist to ./frontends-content') {
			steps {
			    ws("/conf-docker/frontends-angular/my-frontends") {
				     sh('rsync -av --delete ./resa-app/dist/resa-app ./frontends-content')
				}
			}
		}
    }
}
