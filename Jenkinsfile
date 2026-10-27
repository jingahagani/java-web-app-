pipeline {
    agent any
 
    tools {
        jdk 'Java21'
        maven 'Maven'
    }
 
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
 
        stage('Build WAR') {
            steps {
                sh 'mvn clean package'
            }
        }
 
        stage('Verify WAR') {
            steps {
                sh 'ls -lh target/*.war'
            }
        }
	
	stage('Deploy to Tomcat') {
	    steps {
		sh '''docker cp target/java-web-app-1.0.war my-tomcat:/usr/local/tomcat/webapps/java-web-app.war'''
	    }
	}
    }
 
    post {
        success {
            archiveArtifacts artifacts: 'target/*.war'
        }
    }
}
