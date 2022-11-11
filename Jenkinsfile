pipeline{

	agent any

	stages {
	stage('Initialize'){
            steps{
                echo "PATH = D:/Programmes/apache-maven-3.8.1/bin:${PATH}"
            }
        }
		stage('Build') {

			steps {
				sh 'mvn clean install'
				sh 'docker build -t anuagnel/mypublicbuilds:mynewapp-new-${BUILD_NUMBER} .'
			}
		}

		stage('Login') {

			steps {
				
				sh 'docker login  -u anuagnel --password-stdin < /home/test/mydockerpwd'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push anuagnel/mypublicbuilds:mynewapp-new-${BUILD_NUMBER}'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
