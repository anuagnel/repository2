
pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('cf3a5fce-42b1-481e-8606-5ae8aca732bc)
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t anuagnel/mypublicbuilds:mynewapp-${BUILD_NUMBER} .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push anuagnel/mypublicbuilds:mynewapp-${BUILD_NUMBER}'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}