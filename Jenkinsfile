pipeline {
  agent {
    docker {
      image 'maven:3.6.3-jdk-11-slim'
    }
  }
  stages {
    stage('build') {
      steps {
        echo 'compiling the code for sysfoo'
        sh 'mvn compile'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'running unit tests....'
            sh 'mvn clean test'
          }
        }

        stage('test-sub1') {
          steps {
            echo 'sub1'
          }
        }

        stage('test-sub2') {
          steps {
            sleep 200
          }
        }

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
