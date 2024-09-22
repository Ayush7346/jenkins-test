pipeline {
	agent any
	
	stages {
		stage('Checkout Github'){
			steps {
				git branch: 'main', credentialsId: 'jen-doc-git', url: 'https://github.com/iQuantC/NodeApp.git'	
			}
		}		
		stage('Install node dependencies'){
			
		}
		stage('Test Code'){
			
		}
		stage('Build Docker Image'){
			
		}
		stage('Push Image to DockerHub'){
			
		}
	}

	post {
		success {
			echo 'Build&Deploy completed succesfully!'
		}
		failure {
			echo 'Build&Deploy failed. Check logs.'
		}
	}
}