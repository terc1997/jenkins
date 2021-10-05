pipeline {
  agent any 
  environment {
    NEW_VERSION = '1.3.0'
    SERVER_CREDENTIALS=credentials('github-credentials')
  }
  stages {
    stage("build") {
      steps{
        echo 'building the application'
        echo "building version ${NEW_VERSION}"
      }
    }
    
    stage("test") {
      when{
        expression{
          BRANCH_NAME == 'main'
        }
      }
      steps{
        echo 'testing the application'
      }
    }
    
    stage("deploy") {
      steps{
        echo 'deploying the application'
        echo "deploying an application of ${SERVER_CREDENTIALS}"
      }
    }
  }
  post {
    always {
       echo 'sending an email to the team after building'
    }
    success{
      echo 'success'
    }
    failure {
      echo 'famous, somethig went wrong'
    }
  }
}
