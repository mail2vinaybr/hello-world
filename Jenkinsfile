pipeline {
	agent {label 'slave1-docker'}
	tools {
		maven "MAVEN"
	}
	stages {
		stage ('checkout'){
			steps {
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mail2vinaybr/hello-world.git']]])
			}
		}
		stage ('BUILD'){
			steps {
				sh 'mvn clean install'
			}
		}
		stage ('DEPLOY') {
		    steps {
		        deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://13.233.149.102:8081/')], contextPath: null, war: '**/*.war'
		    }
		}
	}
}
