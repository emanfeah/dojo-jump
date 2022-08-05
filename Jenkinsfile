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
				sh 'docker login'
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