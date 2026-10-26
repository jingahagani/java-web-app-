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
    }
 
    post {
        success {
            archiveArtifacts artifacts: 'target/*.war'
        }
    }
}
