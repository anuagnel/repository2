
pipeline{

	agent any

	stages {

		stage('Build') {

			steps {
				sh 'mvn clean install'
				sh 'docker build -t anuagnel/mypublicbuilds:mynewapp-${BUILD_NUMBER} .'
			}
		}

		stage('Login') {

			steps {
				
				sh 'docker login  -u anuagnel --password dckr_pat_PMwgU2kcIKjS_yYwTP85Pd18NEI'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push anuagnel/mypublicbuilds:mynewapp-j-${BUILD_NUMBER}'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}