pipeline {
  agent any
  stages {
    stage('check out') {
      steps {
        git(url: 'https://github.com/xinhuey/maven-samples-A6.git', 
          branch: 'master',
          credentialsId: 'xhw-a6'
        )
      
      }
    }

    stage('git bisect') {
      steps {
        bat 'git bisect start'
        bat 'git bisect bad 1986446'
        bat 'git bisect good 98ac319'
        bat 'git bisect run mvn clean test -Dmaven.compiler.source=8 -Dmaven.compiler.target=8 -Dmaven.compiler.release=8'
        bat 'git bisect reset'
      }
    }

    stage('run') {
      steps {
        bat 'mvn verify -Dmaven.compiler.source=8 -Dmaven.compiler.target=8 -Dmaven.compiler.release=8'
      }
    }

  }
  tools {
    maven 'maven1'
    jdk 'Java_25'
  }
}