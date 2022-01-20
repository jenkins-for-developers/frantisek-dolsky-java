pipeline {
  agent any

  options {
    timestamps()
    buildDiscarder logRotator(artifactDaysToKeepStr: '14', artifactNumToKeepStr: '100', daysToKeepStr: '60', numToKeepStr: '1000')
  }

  stages {

    stage ('Build') {
      steps {
        withMaven(jdk: 'OpenJDK 8', maven: 'Maven 3') {
          sh "mvn clean verify"
        }
      }
    }

    stage ('Verify version') {
      steps {
        sh """java -jar target/moje-apka-*.jar --version"""
      }
    }
  }
}
