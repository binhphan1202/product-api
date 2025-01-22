pipeline {
  agent any
  stages {
    stage('Build') { 
      steps {
        bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }
    stage('Test') { 
      steps {
        echo "************ MUnit test cases execution *************"
      }
    }
    stage('Deployment') { 
      environment {
      	CLIENT_ID = credentials('DEV_CLIENT_ID')
      	CLIENT_SECRET = credentials('DEV_CLIENT_SECRET')
      }
      steps {
        bat 'mvn -U -V -e -B -DskipTests clean deploy -Pdev -DmuleDeploy -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret="%CLIENT_SECRET%" -s settings.xml' 
      }
    }
  }
}