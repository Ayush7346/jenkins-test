pipeline {
	agent any
	
	environment {
	 build = 0.1 
	}
	x
	stages {
		stage('Checkout Github'){
			steps {
				git branch: 'main', credentialsId: 'jenkins-test-git', url: 'https://github.com/Ayush7346/jenkins-test.git'
			}
		}		
		stage('Docker Build'){
			steps {
		        echo "Hello Docker Build"
			    sh "docker build -t  flask-app:${build}"
			}
		}
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