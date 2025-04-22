pipeline {
    agent any
  
    tools{
      maven 'maven 3.9.9'
    }
    stages {
        stage('Build') {
            steps {
                echo 'compile maven app'
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo 'test maven app'
                sh 'mvn clean test'
            }
        }
        stage('Package') { 
            steps {
                echo 'package maven app'
                sh 'mvn package -DskipTests'
            }
        }
    }
}
