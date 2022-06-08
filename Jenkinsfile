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
            sh 'mkdir sparkjava'
            pwd(tmp: true)
            dir(path: 'sparkjava/')
            git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'master')
            sh 'mvn clean install'
            archiveArtifacts 'target/*.war'
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