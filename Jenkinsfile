properties([pipelineTriggers([githubPush()])])

pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-creds')
    }

    parameters {
        booleanParam(defaultValue: false, description: 'Set Value to True to Initiate Destroy Stage', name: 'destroy')
    }

    stages {
        
        stage ("mvn build") {
            steps {
                sh ('mvn clean') 
            }
        }
        stage ("mvn install") {
            steps {
                sh ('mvn install') 
            }
        }

        
        
    }

//     post {
//         always {
//             script {
//                 if (currentBuild.currentResult == 'FAILURE') {
//                 step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: "vinay93avk@gmail.com", sendToIndividuals: true])
//                  }
//             }
//         }
// }
}