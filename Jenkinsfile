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
   echo "$GIT_BRANCH"
   }
  }
  
  stage('02-Build') {
   steps {
    sh '''if [ $GIT_BRANCH == 'develop' ];then
	   echo "deploying to staging";
	   elif [ $GIT_BRANCH == 'master' ];then
	   echo "deploying to prod";
	   else
	   	echo "deploying PR to dev";
	   fi'''
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
