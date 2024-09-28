pipeline {
	agent any
	
	environment {
	 build = 0.1 
	 registry = "tempdockhub/mypythonapp"
	 dockerImage = ''
	}
	
	stages {
		stage('Checkout Github'){
			steps {
				git branch: 'main', credentialsId: 'jenkins-test-git', url: 'https://github.com/Ayush7346/jenkins-test.git'
			}
		}
		stage('Building image') {
          steps{
            script {
              env.PATH = "/usr/local/bin:${env.PATH}"
              sh 'docker --version'
              dockerImage = docker.build registry
            }
          }
        }
		// stage('Docker Build'){
		// 	steps {
		//        script {
		//          withDockerRegistry(credentialsId: '83e52f80-e3d9-4688-98e7-6f323ce15f96') {
		//           sh "docker build -t tempdockhub/jenkins:123"
		//          }
		        
		//        }
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