pipeline {
    agent {
        label 'node-agent-1'
    }
    tools { 
        gradle 'gradle4'
    }
    stages {
      stage('checkout') {
        steps {
          checkout scm
        }
      }
      stage('build') {
        steps {
          echo "Path is" + env.PATH
          sh "gradle build"
        }
      }
    }
}
    
