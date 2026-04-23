pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Approval Email') {
            steps {
                script {
                    emailext(
                        to: 'ganeshmotamarri530@gmail.com',
                        subject: "Approval Required: New Commit Triggered - ${env.JOB_NAME}",
                        body: """
Hello,

A new commit has been pushed to GitHub and Jenkins pipeline has started.

Job Name   : ${env.JOB_NAME}
Build No   : ${env.BUILD_NUMBER}
Build URL  : ${env.BUILD_URL}

Please review and approve the deployment in Jenkins.

Regards ,
Jenkins
"""
                    )
                }
            }
        }

        stage('Wait For Approval') {
            steps {
                input message: 'Approve this build to continue?', ok: 'Approve'
            }
        }

        stage('Next Stage') {
            steps {
                echo 'Approval received. Continuing pipeline...'
            }
        }
    }
}
