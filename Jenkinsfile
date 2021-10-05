pipeline {
  agent any 
  environment {
    NEW_VERSION = '1.3.0'
    SERVER_CREDENTIALS=credentials('github-credentials')
  }
  parameters {
    string(name: 'VERSION',defaultValue:'',description: 'version to deploy on prod')
    choice(name: 'VERSION', choices:['1.1.0','1.2.0','1.3.0'], description:'')
    booleanParam(name:'executeTests',defaultValue:true,description:'')
  }
  
  stages {
    stage("build") {
      steps{
        echo 'building the application'
        echo "building version ${NEW_VERSION}"
      }
    }
    
    stage("test") {
      when {
        expression {
          params.executeTests
        }
      }
      steps {
        echo 'testing the application'
      }
    }
    
    stage("deploy") {
      steps {
        echo 'deploying the application'
        echo "deploying an application of ${params.VERSION}"
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
