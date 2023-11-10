pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/Rxelxius/JenkinsDependencyCheckTest.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			}
		}
		// stage('OWASP Dependency-Check Vulnerabilities') {
		// 	steps {
		// 		dependencyCheck additionalArguments: ''' 
		// 					-o './'
		// 					-s './'
		// 					-f 'ALL' 
		// 					--prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
				
		// 		dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		// 	}
		// }
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}