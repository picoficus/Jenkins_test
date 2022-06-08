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
            git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'main')
            sh 'mvn clean install'
          }
        }

      }
    }

    stage('?') {
      steps {
        sleep 1
      }
    }

    stage('End') {
      steps {
        sleep 1
      }
    }

  }
}