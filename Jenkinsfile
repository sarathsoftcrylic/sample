pipeline {
 agent {
  label 'jenkins-slave.lucktastic.com'
 }
 triggers {
  pollSCM 'H/4 * * * *'
 }
 tools {
  maven 'default'
 }

 stages {
 stage('01-Environment settings') {
   steps {
   echo "Received inputs are , \nJenkins node : jenkins-slave.lucktastic.com \nBuild tool: Maven\n"
   echo "env.BRANCH_NAME"
   }
  }
  
  stage('02-Build') {
   steps {
    sh 'mvn clean install'
   }
  }
 }
 post {
  success {
   echo 'Success, Sending slack notification'
  }
  failure {
   echo 'Failure, Sending slack notification'
  }
 }
}
