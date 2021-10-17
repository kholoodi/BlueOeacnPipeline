pipeline {
  agent any
  stages {
    stage('CodeCollection') {
      steps {
        git(url: 'https://github.com/kholoodi11/simpleMavenJunit.git', changelog: true, poll: true, branch: 'master')
      }
    }

    stage('Compile') {
      steps {
        sh '''mvn clean
mvn compile'''
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }

    stage('ReportPublish') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

  }
}

