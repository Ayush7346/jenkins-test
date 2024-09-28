pipeline {
	agent any
	
	environment {
	 build = 0.1 
	 registry = "tempdockhub/mypythonapp"
	 registryCredential = '83e52f80-e3d9-4688-98e7-6f323ce15f96'
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
              env.PATH = "/usr/local/bin:${env.PATH}" //Adding docker path to jenkins
              sh 'docker --version'
              dockerImage = docker.build registry
            }
          }
        }
		 stage('Upload Image') {
         steps{    
             script {
                sh 'docker --version'
                docker.withRegistry( '', registryCredential ) {
                dockerImage.push()
                }
            }
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