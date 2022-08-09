pipeline{
	
	agent any
	
	environment {
		DOCKERHUB_CREDENTIALS=credentials('my-docker')
	}
	
	stages{
		
		stage('Build') {
			
			steps {
				sh 'docker build -t suryash/jenkins-docker:1.0 .'
			}
		}
		
		stage('Login') {
			
			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Push') {
			
			steps {
				sh 'docker push suryash/jenkins-docker:1.0'
			}
		}
	}
	
	post {
		always {
			sh 'docker logout'
		}
	}
}
