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
          sh 'run gradle test'
         // junit 'build/reports/**/*.xml'
      }
      stage ('func-test') {
          tests = ["one" :{node  { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar one-jar 'First jar!'" }},
          "two" : { node { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar second-jar 'Second jar!'" }},
          "three" : { node { sh "test-data/int-test.shbuild/libs/oto-gradle-1.0.jar third-jar 'Third jar!'" }} ]
      }
      parallel tests
    }
}
