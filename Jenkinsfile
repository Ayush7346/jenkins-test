pipeline {
	agent any
	
	stages {
		stage('Checkout Github'){
			steps {
				git branch: 'main', credentialsId: 'jenkins-test-git', url: 'https://github.com/Ayush7346/jenkins-test.git'
			}
		}		
		// stage('Install node dependencies'){
		// 	steps {
			
		// 	}
		// }
		// stage('Test Code'){
		// 	steps {
		// 	}
		// }
		// stage('Build Docker Image'){
		// 	steps{
		// 	}
		// }
		// stage('Push Image to DockerHub'){
		// 	steps {
		// 	}
		// }
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