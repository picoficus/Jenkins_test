pipeline {
  agent any
  stages {
    stage('Test 1') {
      parallel {
        stage('Test 1') {
          steps {
            sh 'touch bonjour'
            echo 'Hello phase de test'
            sh 'mvn clean test'
          }
        }

        stage('build') {
          steps {
            sh 'git clone https://github.com/kliakos'
            sh 'cd sparkjava-war-example'
            sh 'mvn clean install'
            archiveArtifacts 'sparkjava/target/*.war'
          }
        }

      }
    }

    stage('reports') {
      steps {
        sleep 1
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('End') {
      steps {
        sh 'echo "Fin des taches, c\'est ok"'
      }
    }

  }
}