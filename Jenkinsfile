def GITHUB_REPO = "https://github.com/gauravumrane29/spring-petclinic.git" 
def GITHUB_BRANCH = "main"
def SUBJECT = "JENKINS NOTIFICATION"
def REPLY_EMAIL = "kunalumrane@gmail.com"

pipeline{
    agent any
    stages{
        stage('clean workspace'){
            steps{
                deleteDir()
            }
        }
        stage('Version checking'){
            steps{
                sh "mvn --version"
                sh "java --version"
            }
        }
        // stage('git checkout'){
        //     steps{
        //         git branch:GITHUB_BRANCH, url: GITHUB_REPO, credentialsId: 'kunalumrane'
        //     }
        // }
        stage('Building project'){
            steps{
                sh 'mvn clean package'
                sh '$?'
            }
        }
        stage ('Start') {
            steps {
                // send build started notifications
                slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")

                // send to HipChat
                hipchatSend (color: 'YELLOW', notify: true,
                    message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
                )

                // send to email
                emailext (
                    subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                    body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                    <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
                    recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                )
            }
        }
    //     stage('Email Notification'){
    //     steps{
    //         script{
    //             FAILED_STAGE=env.STAGE_NAME
    //             emailext attachLog: true,
    //             body: "Successfull\n\nBuild URL: ${BUILD_URL} \n\n Build: ${BUILD_NUMBER} Build_ID:${BUILD_ID}" ,
    //             to: "${REPLY_EMAIL}",
    //             from: "Jenkins",
    //             subject: "${SUBJECT} - Build Sucessfull."
    //         }
    //     }
    
    // }
    }
}
