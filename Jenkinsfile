pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Mastoura-dockerhub-token')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t mastoura/RunWay:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push mastoura/RunWay:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}