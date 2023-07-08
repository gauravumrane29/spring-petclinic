pipeline{
    agent any
    parameters{

    }
    stages{
        stage('git checkout'){
            steps{
                script{
                    FAILED_STAGE=env.STAGE_NAME
                }
                deleteDir()
                git branch: main, url: 'https://github.com/gauravumrane29/spring-petclinic.git', credentialsId: 'GithubToken'
            }
        }
        }
    }
