#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    } 
	 stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t shanem/spring-petclinic:latest .'
      }
    }

	stage('Docker Run') {
      agent any
      steps {
        sh 'docker run -it -d -p 8081:8080 shanem/spring-petclinic:latest'
      }
    }

  }
}
