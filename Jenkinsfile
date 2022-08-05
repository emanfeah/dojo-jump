pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('eman-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t emanfeah/dojo-jump:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push emanfeah/dojo-jump:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}