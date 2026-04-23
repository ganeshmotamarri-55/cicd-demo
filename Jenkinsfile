pipeline {
 agent any

 triggers {
   githubPush()
 }

 stages {

   stage('Checkout') {
     steps {
       git branch: 'main',
       url: 'https://github.com/ganeshmotamarri-55/cicd-demo.git'
     }
   }

   stage('Deploy DEV') {
     steps {
       echo 'Deploying to DEV'
       sh 'cat app.txt'
     }
   }

   stage('Approval') {
     steps {
       input message: 'Approve promotion to QA?', ok: 'Approve'
     }
   }

   stage('Tag Release') {
     steps {
       sh 'git tag release-${BUILD_NUMBER}'
       sh 'git push origin --tags'
     }
   }

   stage('Deploy QA') {
     steps {
       echo 'Deploying same approved version to QA'
     }
   }
 }
}
