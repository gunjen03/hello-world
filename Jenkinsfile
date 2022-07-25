properties([pipelineTriggers([githubPush()])])

pipeline {
    agent any

    environment {
        PATH     = "/opt/maven/bin:$PATH"
    }

    // parameters {
    //     booleanParam(defaultValue: false, description: 'Set Value to True to Initiate Destroy Stage', name: 'destroy')
    // }

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
        stage ("tomcat deploy") {
            steps {
                sshagent(['tomcat']) {
                 sh  "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@44.195.31.102:/usr/share/tomcat/webapps"
    // some block
}
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