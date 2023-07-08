
def GITHUB_REPO = "https://github.com/gauravumrane29/spring-petclinic.git" 
def GITHUB_BRANCH = "main"
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
        stage('git checkout'){
            steps{
                script{
                    FAILED_STAGE=env.STAGE_NAME
                }
                git branch:GITHUB_BRANCH, url: GITHUB_REPO, credentialsId: 'kunalumrane'
            }
        }
    }
}
