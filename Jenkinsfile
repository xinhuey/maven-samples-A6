pipeline {
  agent any
  stages {
    stage('check out') {
      steps {
        git(url: 'https://github.com/xinhuey/maven-samples-A6.git', 
          branch: 'master',
          credentialsId: 'xhw-a6')
      
      }
    }

    stage('git bisect') {
      steps {
        bat 'git bisect start'
        bat 'git bisect bad 1986446'
        bat 'git bisect good 98ac319'
        bat 'git bisect run mvn clean test'
        bat 'git bisect reset'
      }
    }

    stage('run') {
      steps {
        bat 'mvn verify'
      }
    }

  }
  tools {
    maven 'maven1'
    jdk 'Java_25'
  }
}