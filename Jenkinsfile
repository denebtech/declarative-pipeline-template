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
      parallel {
        stage('Test On Windows') {
          steps {
            echo "Running tests on Windows"
          }
        }
        stage('Test On Linux') {
          steps {
            echo "Running tests on Linux"
          }
        }
      }
    }
    stage("Confirm deploy to staging") {
      steps {
        timeout(time: 60, unit: "SECONDS") {
          input(message: "Okay to deploy?", ok: "Let\'s do it!")
        }
      }
    }
    stage("Deploy to staging") {
      steps {
        echo "Deploying to staging..."
      }
    }
  }
}
