pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compiling the code for sysfoo'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'running unit tests....'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'generating artifacts....'
        sh 'mvn package -DskipTests'
        archiveArtifacts 'target/*.war'
      }
    }

  }
  tools {
    maven 'maven 3.9.6'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}