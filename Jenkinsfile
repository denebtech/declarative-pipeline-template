pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'chmod a+x run_build_script.sh'
        sh './run_build_script.sh'
      }
    }
    stage('Test') {
      paralell {
        stage("Test on windows") {
          steps {
            echo "Running tests on windows"
          }
        }
        stage("Test on linux") {
          steps {
            echo "Running tests on linux"
          }
        }
      }
    }
  }
}
