pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                script{
                    FAILED_STAGE=env.STAGE_NAME
                }
               
                git branch: main, url: 'https://github.com/gauravumrane29/spring-petclinic.git', credentialsId: 'GithubToken'
            }
        }
        }
    }
