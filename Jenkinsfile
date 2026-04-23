pipeline {
 agent any

 triggers {
   githubPush()
 }

 stages {

   stage('Test') {
     steps {
       bat 'echo Webhook triggered pipeline'
     }
   }

   stage('List Files') {
     steps {
       bat 'dir'
     }
   }
 }
}
