pipeline {
	agent any
	tools{
	    maven 'maven_3_6_3'
	}
	stages {
	    stage('Checkout'){
	        steps{
	          checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'd4862313-4888-4d5b-aaab-2f47d0535bed', url: 'C:\\Users\\Tarun Sharma\\Desktop\\project1\\jpetstore-6']]])
	        }
	    }
		stage ('Build'){
			steps{
				bat 'mvn clean install '
			}
    	}
    	stage('Deploy'){
    	    steps{
    	        deploy adapters: [tomcat9(credentialsId: 'd4862313-4888-4d5b-aaab-2f47d0535bed', path: '', url: 'http://localhost:8086')], contextPath: 'jpetstore-6', war: '**/*.war'
    	    }
    	}
	}
}