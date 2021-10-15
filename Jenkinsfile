pipeline {
    agent any
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
      stage ('unit-test') {
          steps {
          //sh '$(gradle4)/bin/gradle test'
          //junit 'build/test-results/junit-platform/*.xml'
        sh 'gradle test'
        junit 'build/test-results/junit-platform/*.xml'
        }
          }
      }
      stage ('func-test') {
          steps {
              script {
          tests = ["one" :{node  { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar one-jar 'First jar!'" }},
          "two" : { node { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar second-jar 'Second jar!'" }},
          "three" : { node { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar third-jar 'Third jar!'" }} ]
                  
         parallel tests
      }
          }
      }
      
    }
    //parallel tests
}
