def GITHUB_REPO = "https://github.com/gauravumrane29/spring-petclinic.git" 
def GITHUB_BRANCH = "main"
def SUBJECT = "JENKINS NOTIFICATION"
def REPLY_EMAIL = "kunalumrane@gmail.com"

pipeline{
    agent any
    environment{
        VERSION = "${env.BUILD_ID}"
    }
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
        stage('Email Notification'){
            steps{
                mail bcc: '', body: "<br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "${currentBuild.result} CI: Project name -> ${env.JOB_NAME}", to: "kunalumrane@gmail.com"; 
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
