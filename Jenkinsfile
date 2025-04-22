pipeline {
  agent any
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
        sh '''# Truncate the GIT_COMMIT to the first 7 characters
GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)

# Set the version using Maven
mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit'''
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'maven 3.9.9'
  }
}