
pipeline{

	agent any

	stages {

		stage('Build') {

			steps {
				bat 'mvn clean install'
				bat 'docker build -t anuagnel/mypublicbuilds:mynewapp-${BUILD_NUMBER} .'
			}
		}

		stage('Login') {

			steps {
				
				bat 'docker login  -u anuagnel --password dckr_pat_PMwgU2kcIKjS_yYwTP85Pd18NEI'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push anuagnel/mypublicbuilds:mynewapp-j-${BUILD_NUMBER}'
			}
		}
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}