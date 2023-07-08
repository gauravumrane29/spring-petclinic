def GITHUB_REPO = "https://github.com/gauravumrane29/spring-petclinic.git" 
def GITHUB_BRANCH = "main"
def SUBJECT = "JENKINS NOTIFICATION"
def REPLY_EMAIL = "gaurav.umrane@gmail.com"

pipeline{
    agent any
    stages{
        stage('clean workspace'){
            steps{
                script{
                    FAILED_STAGE=env.STAGE_NAME
                }
                deleteDir()
            }
        }
        stage('Version checking'){
            steps{
                sh "mvn --version"
                sh "java --version"
            }
        }
        stage('git checkout'){
            steps{
                script{
                    FAILED_STAGE=env.STAGE_NAME
                }
                git branch:GITHUB_BRANCH, url: GITHUB_REPO,
            }
        }
        stage('Building project'){
            steps{
                sh 'mvn clean package'
                sh '$?'
            }
        }
        stage('Email Notification'){
        steps{
            script{
                FAILED_STAGE=env.STAGE_NAME
                emailext attachLog: true,
                body: "Successfull\n\nBuild URL: ${BUILD_URL} \n\n Build: ${BUILD_NUMBER} Build_ID:${BUILD_ID}" ,
                to: "${REPLY_EMAIL}",
                subject: "${SUBJECT} - Build Sucessfull."
            }
        }
    }
    }
}
