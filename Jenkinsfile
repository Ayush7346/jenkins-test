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
                sh 'docker login -u tempdockhub -p dckr_pat_YC2zOSrDCO4SqZGZDI99gV_xGKE'
                sh 'echo ${dockerImage}'
                sh 'docker build -t tempdockhub/myapp:0.1 .'
                sh 'docker push tempdockhub/myapp:0.1'
                }
            }
          }
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
